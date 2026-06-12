---
title: "My computer start on a Grub Prompt"
date: 2021-07-29
forum: Installation &amp; Upgrades
---

### Post by francois7500 on 2021-07-29
Hello, 

Excuse me per advance for my language, i am not native English .

Like i say in the title, i  have problem with my computer, when i start the computer he start on a grub prompt . I have already try to fix it with Boot Repear but nothing change . 

What can i do else to fix it ? what kind of information did you need ? 

Here the information i can give you right know : the computer in under Ubuntu 16.04 . The system are separated on two disk, on my SSD i have almost all the system, the /home is on a other disk . Also ther two disk are encrypt with the same password and when i start the computer i have to enter the password to unlock the two disk and start the system . 

PS: I know my system is old but i cannot change it at the moment, i will do in the future .

Thanks you per advance form your help, have a good day .

---

### Post by mIk3_08 on 2021-07-29
Your Operating System that you are using now is just out of support just until this April 2021. But maybe other here in the community might consider helping you if they already encounter same problem as you do. 
But then again, just want to remind you that your Operating System is already out of support right now. so, just wanna make you understand it. Good Luck.

---

### Post by yancek on 2021-07-29
>   what kind of information did you need ? 
  

Run boot repair with the Create Bootinfo Summary option and post the link you get when it finishes.  That will have the information needed for someone to help.

---

### Post by francois7500 on 2021-08-04
Hello, 

Thanks to you two for your answer . 

Here the link ask by Yancek : [http://paste.ubuntu.com/p/gv5KzWt7rg/](http://paste.ubuntu.com/p/gv5KzWt7rg/) .

Thanks to anyone can help me . 

Have a good day .

---

### Post by oldfred on 2021-08-04
System not that old as it is UEFI.

Report did not show some info that is normally in / like grub.cfg & fstab.
You have to mount lvm & decrypt install before report or repair.
But repairs will not work as repository for 16.04 is closed. EoL 21-04. The LTS versions are only for 5 years.
(actually surprised Boot-Repair worked at all as it is only for current versions of Ubuntu).

Do you have good backups? 
With encryption that is a requirement.
And if not, that is the first thing you need to do.

---

### Post by francois7500 on 2021-08-04
Hello Oldfred, 

I try to do what you tell me but after i have  mount lvm and decrypt them, i launch boot-repair and he tell me to  decrypt my partition but they already decrypt ?! can you help me ith  that please ?

---

### Post by tea for one on 2021-08-04
[COLOR="#0000FF"]oldfred[/COLOR] is asking if you have back-ups of your data.

If you do not have back-ups, then that is your first priority.

Boot-repair will **not** fix your boot problem because you are using Ubuntu 16.04, which is unsupported.

When you have back-ups of your data, you should install a supported version of Ubuntu i.e. 20.04 LTS (Long Term Support)

---

### Post by francois7500 on 2021-08-04
Okay but i need  help to fix my problem, i can if i need backup my data, is it another way to fix my issues ?

---

