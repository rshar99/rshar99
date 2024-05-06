- 👋 Hi, I’m @rshar99
class Employee:
    def __init__(self, name, rating, experience):
        self.name = name
        self.rating = rating
        self.experience = experience

def custom_sort_key(emp):
# Primary criterion: Sort by performance rating (descending)
# Secondary criterion: Sort by years of experience (ascending) if ratings are tied
# Tertiary criterion: Sort by name (alphabetically ascending) if ratings and experience are tied
    return (-emp.rating, emp.experience, emp.name)

def sort_employee_records(records):
# Create Employee objects from records
    employees = [Employee(*record) for record in records]
    
# Sort employees using custom key
    sorted_employees = sorted(employees, key=custom_sort_key)
    
# Return sorted employee records as tuples
    return [(emp.name, emp.rating, emp.experience) for emp in sorted_employees]

# Sample employee records
records = [
    ("Ross", 8, 5),
    ("Rachel", 7, 3),
    ("Joey", 8, 7),
    ("Chandler", 9, 4),
    ("Pheobe", 7, 5),
    ("Monica", 9, 3)
]

# Sort employee records based on specified criteria
sorted_records = sort_employee_records(records)

# Display sorted records
print("Sorted Employee Records:")
for record in sorted_records:
    print(f"Name: {record[0]}, Rating: {record[1]}, Experience: {record[2]} years")
