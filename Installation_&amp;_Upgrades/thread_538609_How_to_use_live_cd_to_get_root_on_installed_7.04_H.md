---
title: "How to use live cd to get root on installed 7.04 HD?"
date: 2007-08-30
forum: Installation &amp; Upgrades
---

### Post by Preserved Killick on 2007-08-30
I want to boot from Live CD Ubuntu 7.04 and run chown root:gdm on a file on the installled HD.  Can you tell me how, please?  Here's why: 

Upgraded from Edgy to Feisty (almost) but I can't get X to run.  Usually I have to run "envy" from a prompt to get the nvidia drivers right.  But this time I can't get to the command prompt.

I got this error: 
"Server Authorization directory (daemon/ServAuthDir) is set to /var/lib/gdm but it is not owned by user root and group gdm.  Please correct the ownership or GDM configuration and restart GDM" [OK]

Then the screen freezes and I can't get to a command prompt.  So I want to run "chown root:gdm /var/lib/gdm" and see if that lets me fix the problem.

Thanks!

Killick

---

### Post by Pumalite on 2007-08-30
First you have to mount your partition:
sudo mkdir /media/ubuntu
sudo mount -t ext3 /dev/sdx /media/ubuntu

---

### Post by Preserved Killick on 2007-08-30
Thanks, Pumalite.  That was what I needed to do.  I note for others that you can also click "Places > Computer" and right-click the drive.  At the prompt, select "mount" to mount the drive.

I was able to change the ownership on the GDM directory.  Now my system is hanging / freezing during the boot for perhaps some other reason.  I've started a thread elsewhere on that one, but I want to thank you for getting me a little further along.

Thank you!

-- Killick

---

### Post by Pumalite on 2007-08-30
You are welcome. If you tell me what's your new problem; maybe I can help you with that too.

---

### Post by Preserved Killick on 2007-08-30
Thank you, Pumalite.

[http://ubuntuforums.org/showthread.php?t=529451](http://ubuntuforums.org/showthread.php?t=529451)

I've joined the above thread to see how to get a command prompt after a boot freeze or hang I'm experiencing.  Apparently I 'm not alone.  :-(

Thanks for offering to help.  Any guidance is welcome!  My /home is backed up on another machine, so if need be, I can simply try to install Feisty from the CD.  But I'm keeping my fingers crossed that this obstacle has a more elegant solution.

-- Killick

---

### Post by Pumalite on 2007-08-30
I'm thinking of a bad burn. Did you do md5sum on your iso? Did you burn at 4x? Have you tried Alternate CD?: [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
Mark box below 'Start Download'

---

### Post by Preserved Killick on 2007-08-30
Hi.  I used sudo apt-get update, sudo apt-get dist-upgrade, so I don't think it's a burn problem if I understand you correctly.  I don't have the alternate CD but I bought at 7.04 CD online.  I didn't realize, when I ordered the disk, that I would have to upgrade to edgy before I could upgrade to feisty.  So when dapper to edgy went well, I decided to try again with feisty.  I have only used the disk as a live CD.

-- Killick

---

### Post by Pumalite on 2007-08-30
After reviewing the thread and reading your link again, I realize my mistake. Sorry. OTOH, if you have /home safe, you can do a fresh install of Feisty, preserving /home. I would recommend it. Upgrades are always messy and your drives get littered with stuff you cannot get rid of.

---

