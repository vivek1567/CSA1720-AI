import heapq
goal_state = (1, 2, 3, 4, 5, 6, 7, 8, 0)

moves = [(0, 1), (0, -1), (1, 0), (-1, 0)]

def get_neighbors(state):
    neighbors = []
    empty_index = state.index(0)
    empty_row, empty_col = empty_index // 3, empty_index % 3
    
    for dr, dc in moves:
        new_row, new_col = empty_row + dr, empty_col + dc
        
        if 0 <= new_row < 3 and 0 <= new_col < 3:
            neighbor_state = list(state)
            neighbor_index = new_row * 3 + new_col
            neighbor_state[empty_index], neighbor_state[neighbor_index] = neighbor_state[neighbor_index], neighbor_state[empty_index]
            neighbors.append(tuple(neighbor_state))
    
    return neighbors

def manhattan_distance(state):
    distance = 0
    for i in range(9):
        if state[i] != 0:
            current_row, current_col = i // 3, i % 3
            target_row, target_col = (state[i] - 1) // 3, (state[i] - 1) % 3
            distance += abs(current_row - target_row) + abs(current_col - target_col)
    return distance

def solve_puzzle(initial_state):
    open_list = [(manhattan_distance(initial_state), initial_state)]
    closed_set = set()
    
    while open_list:
        current_state = heapq.heappop(open_list)[1]
        if current_state == goal_state:
            return current_state
        
        closed_set.add(current_state)
        for neighbor in get_neighbors(current_state):
            if neighbor not in closed_set:
                heapq.heappush(open_list, (manhattan_distance(neighbor), neighbor))
    
    return None

initial_state = (1, 0, 3, 4, 2, 5, 7, 8, 6)
solution = solve_puzzle(initial_state)

if solution:
    print("Solution found:")
    for i in range(0, 9, 3):
        print(solution[i:i+3])
else:
    print("No solution found.")
