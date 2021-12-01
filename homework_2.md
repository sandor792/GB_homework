#1
my_list = [1, 2, -77, 'True', False, 777]
def my_type(el):
    for el in range(len(my_list)):
        print(type(my_list[el]).name)
    return
my_type(my_list)

#2
items = input("Укажите значения списка через запятую >>> ").split(",")
max_idx = len(items) - 1
for idx in range(0, max_idx, 2):
    next_idx = idx + 1
    items[idx], items[next_idx] = items[next_idx], items[idx]
print(items)

#3
month = int(input("Укажите номер месяца >>> "))
year_dict = {
    "зима": (12, 1, 2),
    "весна": (3, 4, 5),
    "лето": (6, 7, 8),
    "осень": (9, 10, 11),}
for season, months in year_dict.items():
    if month in months:
        print(f"Время года = {season}")

#4
words = input("Введите строку из нескольких слов >>> ").split()
for idx, value in enumerate(words, start=1):
    print(f"{idx}. {value[:10]}")

#5
rating = [9, 8, 8, 7, 6, 6, 6, 5, 3, 2, 1]
while True:
    try:
        print(f"Рейтинг = {rating}")
        user_rate = int(input("Введите новый рейтинг >>> "))
        current_rate_count = rating.count(user_rate)
        if current_rate_count:
            last_current_idx = rating.index(user_rate) + current_rate_count
            rating.insert(last_current_idx, user_rate)
        else:
            if user_rate > rating[0]:
                rating.insert(0, user_rate)
            elif user_rate < rating[-1]:
                rating.append(user_rate)
            else:
                for idx, rate in enumerate(rating):
                    if rate < user_rate:
                        rating.insert(idx, user_rate)
                        break
        print(rating)
    except ValueError:
        print("Неверное число")
    except KeyboardInterrupt:
        exit()

 #6
       product_structure = {
    "Название": str,
    "Цена": int,
    "Количество": int,
    "Единица измерения": str,}
product_list = []
product_counter = 1
while True:
    decision = input(f"Товаров = {len(product_list)}, добавить? [y/n] ").lower()
    if decision == 'n':
        break
    else:
        product_info = {}
        for property_name, property_type in product_structure.items():
            user_input = input(f"Заполните поле '{property_name}' >>> ")
            product_info[property_name] = property_type(user_input)
        product_list.append((product_counter, product_info))
        product_counter += 1
product_analytics = {}
for analytics_key in product_structure.keys():
    item_list = []

    for product in product_list:
        item_list.append(product[1][analytics_key])

    product_analytics[analytics_key] = set(item_list)

print(product_analytics)
