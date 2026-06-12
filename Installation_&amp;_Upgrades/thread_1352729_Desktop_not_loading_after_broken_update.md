---
title: "Desktop not loading after broken update"
date: 2009-12-11
forum: Installation &amp; Upgrades
---

### Post by nagpai on 2009-12-11
:(

Warning: I am relatively a newbie.

Hi, I had a perfectly running karmic koala on my dell vostro laptop until i attempted to upgrade my packages using upgrade manager. 

The process froze and i had broken packages. After that the system always boots in command prompt after showing GRUb options and the white logo.

I managed to browse through the forums and fix all the broken packages. However, when i boot it always boots in the text mode and doesnt load the Graphic Gnome desktop.

I have already removed and installed graphic desktop... How do i get the screen back!?

---

### Post by byStanderone on 2009-12-12
...have you done a system restore already?

---

### Post by nagpai on 2009-12-12
nope i havent :(..

---

### Post by nagpai on 2009-12-12
I am sure there would be some simple way to bail out of this command prompt hell.

After the white logo i am prompted for user name and password in command prompt itself.

dunno whats gone wrong.

---

### Post by byStanderone on 2009-12-12
...try a system restore first and see what happens, select this option on the grub menu when it prompts up.

---

### Post by nagpai on 2009-12-13
Managed to solve it finally :)

took some good help from the #ubuntu-beginners IRC chat.

Here is what i did

After booting and logging in through the tty1 command prompt, i typed:

startx

the GUI desktop loaded. 

I reinstalled xorg and gnome desktop components through synaptic package manager..

and it worked :)

Thanks so much for your response, Standerone

---

### Post by byStanderone on 2009-12-13
ok...don't forget to mark your thread as solved, helps a lot when searching for solutions. thanks as well.

---

