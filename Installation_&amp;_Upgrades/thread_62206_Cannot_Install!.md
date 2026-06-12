---
title: "Cannot Install!"
date: 2005-09-03
forum: Installation &amp; Upgrades
---

### Post by FinalFan on 2005-09-03
Hi, I've just received my Ubuntu CD's and I plan on installing it on an older PC I own. The problem is, it can't boot from CD's. 

I have already looked in the wiki and saw the topic about making a boot floppy with the 'Smart Boot Manager'. So, I made the floppy like the topic said. However, after the Smart Boot Manager menu appeared and I selected 'CD-ROM' (like the wiki said) it gave me the following error message: "Error: 0xAA". 

After that, I've tried other ways to install Ubuntu, like that way that said to install from windoze. Now, the problem here is that it tells me to edit a line in "C:\Boot.ini". I do not have this file. I've made all files visible and searched for it, but no avail.... I know I was supposed to have but I do not. (My Operating System on that PC is Windoze 98SE). 

Is there another way to install Ubuntu!? Or is it possible forme to create an alternative boot floppy capable of booting Ubuntu?

---

### Post by ZombieCat on 2005-09-03
You'll need to go to Tools>Folder Options...>View and uncheck Hide protected operating system files. Then boot.ini should show up in C:\. Once you can see it, you'll need to open its properties and uncheck Read-only so that you can actually make changes to it.

---

### Post by FinalFan on 2005-09-04
I've already tried that, but the file still won't appear. I have even used the Windoze Search to try looking for it but still... no boot.ini. Is it because the O.S is Windoze 98SE?

Isn't there a pre-made boot disk I can download to boot from the CD-ROM? Something like Windoze Boot Disk?

---

### Post by ZombieCat on 2005-09-05
Whoops, my bad. I'm using XP, figured the process would be the same. Well, supposedly, the Install CD should start on reboot and you can go from there ... but oddly enough, I'm having the same problem. Can't install from the CD. You could try downloading the LiveCD version, if you haven't already, but you might encounter the same problem ... I know I did ... Hmm, dang. You've already tried installing from the harddrive ... every other install process I see requires to either have Linux on a seperate networked computer, or access to specialized hardware.

Don't know what else to say, man. I've only used Mandrake, so I'm a total newb at Ubuntu. Hopefully someone with some actual knowledge will ... see this post .... eventually .....

---

### Post by elgx on 2005-09-05
i have another kind of problem with the installation of the os itself.
i'm using an intel celeron, no dual boot, no problems with compatibility, nothing until now. a part from sound never working on linux (fedora and then ubuntu, while when i had windows 2000 it worked fine).

during installation ubuntu asks me not once, not twice, but FOREVER, to insert an username and a passwd. and as result i never have a working uid.
i tried "adduser" from rescue mode, but does sth similar to
" added user elena
added home /home/elena
removed home /home/elena
removed user elena"
....
first time i installed ubuntu, this problem did not come.
but from the second, it comes everytime i try to install this wonderful OS... ;_;

none of you had (and solved) this problem? it is so annoying. i actually DO NOT have any os installed on my pc....

excuse me for my english... thank you all ^^

---

### Post by elgx on 2005-09-05
ok, i finally managed to enter a user id.
but the home folder is not in /home/... but in /my_home, it was the only possibility.
logged into gdm.
my user... is not a sudoer. i cannot do nothing now. neither create a new user account. i will have to redo the full installation? can anyone help me?
pleeeeeeeease! ](*,)  ](*,)

---

