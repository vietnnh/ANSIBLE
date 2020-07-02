---
- name: dat ip cho loobpack
  hosts: all # tên của thiết bị trong Ansible server( vì ở đây chỉ có router nên có thể để all)
  gather_facts: no
# các tác vụ
  tasks:
    - name: Set loopback IPv4 address # Đặt tên task để quản lý
      ios_l3_interface: # do cấu hình router nên bắt buộc khai báo như vậy
      interface_id: "{{ item.number }}"
      ipv4: "{{ item.name }}"
      state: present

      with_items:
        - { number: loopback 1, name: "192.168.1.1/24" }
        - { number: loopback 2, name: "192.168.2.1/24" }
        - { number: loopback 3, name: "192.168.3.1/24" }

     name: Show ip
      ios_command: # Viết lệnh để gửi ở mode command line của router
        commands:
          - show ip int brief
      register: show_ip # gắn kết quả vào biến show_ip

    - debug: var=show_ip.stdout_lines # debug: in ra màn hình, đặt biến var(lấy thông tin của các dòng từ show_ip gắn vào),in biến var
