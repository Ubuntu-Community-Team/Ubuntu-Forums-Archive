---
title: "[SOLVED] Changing Order of OS Boot"
date: 2008-08-22
forum: Installation &amp; Upgrades
---

### Post by katzkoll on 2008-08-22
I would like to change the order of the OS Boot program.  When I installed Ubuntu, it gave it the priority  (1st) location and I would like Windows to have that spot with Ubuntu second.  This is only because I "have to use" Window because of specific programs that will not work under Wine.  

How can I change or edit this program?

---

### Post by sakthi on 2008-08-22
Open the file: /boot/grub/menu.lst

Change the order by changing the number in the line "default". For example, if you have two options in the grub then it is numbered as 0 and 1. If Windows comes second then put 1 and above line looks as "default 1".

Hope that helps!

---

### Post by katzkoll on 2008-08-22
I am sorry, but I am a real novice.  What is the "grub" and how do I find it and change it?

---

### Post by OutOfReach on 2008-08-22
GRUB is the bootloader where you choose the OS to boot to.

---

### Post by katzkoll on 2008-08-22
How do you "Open" the grub file?  I am currently in Windows.  Do I need to go to Ubuntu to open and change this file?

---

### Post by fmartinez on 2008-08-22
Here's a step by step: 
1. Applications -> Accessories -> Terminal
2. Type the command below:
[html]sudo gedit /boot/grub/menu.lst[/html]
3. You will prompted for the Admin(Root User) password. Usually it's your own password
4. A text application (gedit) will open up and display the contents of the menu.lst file with Root permissions allowing you to make the changes that sakthi recommended. 

Hope this helps.

---

### Post by sakthi on 2008-08-22
Yes boot into Ubuntu, open that file with an editor of your choice and then make the changes and save it.

---

### Post by katzkoll on 2008-08-22
Thanks to everyone for your help.  I was successful at changing the boot order.  Now if I only did not have to use Windows!!!:)

---

### Post by fixinmaniac on 2008-08-22
real newbie here (about 4 days in) - don't mean to be dense but i had already found the boot menu list - and wish as well to change the order - but there are no numbers next to the entries - do you mean for me to copy/paste the entry for win loader above the ubuntu in the list?

---

### Post by DavidTangye on 2008-08-22
> **fmartinez said:**
> 3. You will prompted for the Admin(Root User) password. Usually it's your own password Just to clarify a minor confusion here: Its not root's password (it does not have one) its yours. You are always prompted for your own password, and given that you are then confirming that its really you at the PC and not a passing vandal, a program (eg the editor) is loaded for you with root's privileges.

---

### Post by DavidTangye on 2008-08-22
> **fixinmaniac said:**
>  do you mean for me to copy/paste the entry for win loader above the ubuntu in the list?Yes but read the menu.lst file carefully. See the line > # Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST and follow this advice. Anything between > ### BEGIN AUTOMAGIC KERNELS LIST and > ### END DEBIAN AUTOMAGIC KERNELS LIST gets wiped and rebuilt the next time the kernel is upgraded.

---

### Post by pastalavista on 2008-08-22
Just so you'll know, if you want a GUI application that makes all this a little easier, you can install QGrubEditor from the repositories.

---

### Post by sakthi on 2008-08-22
> **fixinmaniac said:**
> real newbie here (about 4 days in) - don't mean to be dense but i had already found the boot menu list - and wish as well to change the order - but there are no numbers next to the entries - do you mean for me to copy/paste the entry for win loader above the ubuntu in the list?

There will not be any numbers assigned for the list of OS in the grub file, but usually the list from top to bottom will be numbered as 0,1,2,3,......

---

