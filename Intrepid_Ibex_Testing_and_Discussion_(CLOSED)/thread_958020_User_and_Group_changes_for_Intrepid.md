---
title: "User and Group changes for Intrepid"
date: 2008-10-24
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Zularan on 2008-10-24
I'm trying to add my username to the 'disk' group for the purpose of setting up Virtualisation as per another [HowTo thread]("http://ubuntuforums.org/showthread.php?t=769883").

The disk group seems to be hidden I guess ?

/dev/sda and /dev/sda1 belong to group 6 which isn't listed on the users and groups dialog and the output of 'sudo cat /etc/group' says

root:x:0:
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:xmyusernamex
tty:x:5:
lp:x:7:
mail:x:8:

Done some googling and searching here and am at a loss as to how to add my user to the disk group for raw access. Only thing that seems to work is making /dev/sda 666 but I'm not sure that's a good permanent solution.

Any insight appreciated

---

