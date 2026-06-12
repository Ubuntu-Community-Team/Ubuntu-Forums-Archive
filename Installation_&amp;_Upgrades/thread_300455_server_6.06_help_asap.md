---
title: "server 6.06 help asap"
date: 2006-11-15
forum: Installation &amp; Upgrades
---

### Post by Cotsuma on 2006-11-15
I need help asap on this if possible. I am near the end of installing ubuntu-6.06.1-server-i386.iso and i got this message and idk what to do.
> 
[!!] Install the base system
Debootstrap warning
waring: file:///cdrom/pool/main/g/gzip/gzip_1.3.5-12_i386.deb was corrupt
<Go Back>             <Continue>

What should i do? Go back or continue?

---

### Post by taurus on 2006-11-15
Did you check the CD before you installed it and how fast did you burn the ISO image anyway?  You can continue and install the gzip later with aptitude/apt-get but you could encounter more packages with similar problem soon!

---

### Post by Cotsuma on 2006-11-15
The speed at which i put it on the cd was 48x Max. Should i go back and cancel it and burn a new cd at a different speed?

---

### Post by taurus on 2006-11-15
Yes, try burning it again at 4x...

---

### Post by Cotsuma on 2006-11-15
I can't do 4x but i can do 8x (1200 KB/sec) will this still do?

---

### Post by taurus on 2006-11-15
It should since I usually burn those ISO images at 8x and so far, everything is installing fine.  So, go for it.

---

### Post by Cotsuma on 2006-11-15
Thank you for your help and i will post any progress in about and hour or so bc i am going to church in a few mins. Again I thank you.

---

### Post by Cotsuma on 2006-11-15
The installation ran smoothly but when it restarted i kept restarting to the same thing over and over again and it never brought me to a log in window. It kept saying, booting grub 
It would then start the loading up process and then would restart a sec or 2 later. Should i try and reinstall again?

---

### Post by taurus on 2006-11-15
Are you installing the server, Dapper, version?

---

### Post by Cotsuma on 2006-11-15
yes i am . The 6.06 drapper version

---

### Post by Cotsuma on 2006-11-15
When i started i clicked Install a LAMP server instead of  Install to the hard disk so that may be the problem

---

### Post by taurus on 2006-11-15
Do you know exactly where it restarts your computer?  What is the last thing you see on the screen before it reboots itself?

---

### Post by Cotsuma on 2006-11-15
the last part of it that i can see b4 it restarts is 

initdr /boot/intrd.img-6.2.15-26-server
  [Linux (something here)]
savedefault
boot

---

### Post by taurus on 2006-11-15
So it's not actually booting or starting any process at all?  It could be something wrong with your GRUB!  When in GRUB, you can press <Esc> to get into it menu and check to see "root=" is pointing to the actual partition where / is!

---

### Post by Cotsuma on 2006-11-15
No, it doesn't start any process or bring up anything. When i press Esc i get 3 things in a box that says

Ubuntu, kernel 2.6.15-26-server
Ubuntu, kernel 2.6.15-26-server (recovery mode)
Ubuntu, memtest86*

---

### Post by taurus on 2006-11-15
See if you can boot into recovery mode and if you can, paste the output of these commands here.

```
fdisk -l
cat /etc/fstab
cat /boot/grub/menu.lst
```

---

### Post by Cotsuma on 2006-11-15
I will try and reinstall it and see if that will work. And i may not reply for the rest of the night bc i have school early in the morning. When i ran the recovery mode it is doing that same thing as the orignal mode.

---

### Post by confused57 on 2006-11-16
There's is a bug with the Dapper server cd on some older hardware:
[http://www.ubuntuforums.org/showthread.php?t=295792](http://www.ubuntuforums.org/showthread.php?t=295792)

You can install a server using the Dapper alternate cd.

I installed the server cd on a 500 Mhz, AMD K6-2, several times and it would just continually reboot the computer...server install with the alternate cd worked fine.
   Installed server cd on a Dell, 2.0 GHz, P4, with no problems.

---

### Post by Cotsuma on 2006-11-19
Ok thank you i will try that and see if it works. Ty

---

### Post by Cotsuma on 2006-11-25
ok The alternate CD did work and all is going well untill it restarts and then it has some text and it wants me to log into the admin root or something like that but it has 
(my_user_name)@Linux:~$ 
What do i put after ~$
i have typed in sudo administrator and then it says:
> 
Password:
And i don't know what the password is suppose to be. I have tried my user name's password but then it says:
> 
sudo: administrator: command not found
(user_name)@Linux:~$


---

### Post by taurus on 2006-11-25
Use the same password that you use to log in with your regular account.

---

### Post by Cotsuma on 2006-11-25
i have tried that and yet it hasn't worked.
it does say that if i want to run "root" commands, i simply prepend sudo in front of it.

I am so lost with this. I want to run an IRCd on this Server. I first need to connect it to my network and then go from there but is there like a desktop type look (with icons ect...)

---

### Post by Cotsuma on 2006-11-25
Tarus are you able to get on IRC or can i pm you for more help?

---

