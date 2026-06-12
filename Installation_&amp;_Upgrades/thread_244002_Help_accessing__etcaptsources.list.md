---
title: "Help accessing  /etc/apt/sources.list"
date: 2006-08-25
forum: Installation &amp; Upgrades
---

### Post by Tully IDDQD on 2006-08-25
Hi, I need to edit my sources.list and while I was having no problem at first, now I get an error message even trying to access said directory. 

tully@tully-desktop:~$  /etc/apt/sources.list
bash: /etc/apt/sources.list: Permission denied


I am new, so I'm sure this is a simple thing...but it is important because I have one faulty line on the list (Wine to be exact) that is making it so the entire thing doesn't work, including my add/remove programs, so I really need some help. Thank you in advance. 

This is the error message I get when trying to access add/remove:
"
Failed to check for installed and available applications

This is a major failure of your software management system. Check the file permissions and correctness of hte file '/etc/apt/sources.list' and reload the sofware information: 'sudo apt-get update'.

"

- Tully

---

### Post by hyb on 2006-08-25
You need to be logged in as root so try typing "su" without the " then your login password and try again but if you're using gnome try "gedit <file>"

---

### Post by meng on 2006-08-25
The command you typed is trying to execute the file, you need to edit the file with your favorite editor, if you don't have a preference try
gksudo gedit /etc/apt/sources.list

---

### Post by Tully IDDQD on 2006-08-25
meng you are a lifesaver, thank you so much.


Only my first day with Linux, and I am loving it so far. Thanks for the replies guys.

---

### Post by true_friend on 2006-08-25
add "sudo" before every linux command in ubuntu/kubuntu/xubntu etc.

---

### Post by randell6564 on 2006-08-25
> **Tully IDDQD said:**
> Hi, I need to edit my sources.list and while I was having no problem at first, now I get an error message even trying to access said directory. 

tully@tully-desktop:~$  /etc/apt/sources.list
bash: /etc/apt/sources.list: Permission denied


I am new, so I'm sure this is a simple thing...but it is important because I have one faulty line on the list (Wine to be exact) that is making it so the entire thing doesn't work, including my add/remove programs, so I really need some help. Thank you in advance. 

This is the error message I get when trying to access add/remove:
"
Failed to check for installed and available applications

This is a major failure of your software management system. Check the file permissions and correctness of hte file '/etc/apt/sources.list' and reload the sofware information: 'sudo apt-get update'.

"

- Tully

Sudo gedit /etc/apt/sources.list is what you want to enter at the terminal.

OR, if you do not use gedit, then,

sudo nano /etc/apt/sources.list

---

### Post by randell6564 on 2006-08-25
> **hyb said:**
> You need to be logged in as root so try typing "su" without the " then your login password and try again but if you're using gnome try "gedit <file>"

You do NOT need to be logged in as root to access /etc/apt/sources.list.

Use 'sudo' at the terminal.

---

