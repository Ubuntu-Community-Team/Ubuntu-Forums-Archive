---
title: "Reinstalling Ubuntu"
date: 2007-09-28
forum: Installation &amp; Upgrades
---

### Post by Dave85 on 2007-09-28
Hi,

After installing Ubuntu 7.04 and it not working probally, i decided to go back and reinstall my orginal copy of Ubuntu.
Only problem is, it's not installing properly. The bias is boot from the CD, and it comes up with the options to start or install ubuntu. Now, when i select this, it seems to start doing things. after about a minute, it comes up with a plale screen and doesn't do anything. Any ideas whats going on? And why the CD doesnt seem to install ubuntu even though its the same CD i orignally installed from.
Any help will be greatly appricated

Regards

-Dave

---

### Post by randytuggle on 2007-09-28
Have you formatted your drive?

---

### Post by Dave85 on 2007-09-28
I havn't tried that yet. What is the command to reformat? Im still new at Linux :)

Although, isn't Ubuntu just installing and running from the CD? so would it make a difference if the hard drive was formatted or not?

---

### Post by randytuggle on 2007-09-28
Before I answer that question, what did you have on the computer prior to this problem? Was it windows? I always use a program command called fdisk. If you do a search on fdisk , you will be able to figure it out easily. I usually open terminal from the live cd and choose "fdisk /dev/hda" (no quotes).

---

### Post by Dave85 on 2007-09-28
Before i have ubuntu on the machine, and before that it had nothing on. The machine was built with the sole purpose of it being a Linux system.

Although, i brought up a terminal (Ctrl+Alt+F1) and typed fdisk /dev/hda but that seem to just restart the installation and bring it back to the pale screen 

:(

any ideas?

---

### Post by randytuggle on 2007-09-28
I'm stuck after that came up. Have you tried creating another CD for the install?

---

### Post by Dave85 on 2007-09-28
So am I :( I haven’t tried making a new CD, but again, I think we are grasping at straws here with every possibility. I can’t see a new CD working any different, considering last time I used the CD, it worked fully. 
Are there other ways to format the hard-drive?

---

### Post by megamania on 2007-09-28
> **Dave85 said:**
> So am I :( I haven’t tried making a new CD, but again, I think we are grasping at straws here with every possibility. I can’t see a new CD working any different, considering last time I used the CD, it worked fully. 
Are there other ways to format the hard-drive?
The last time this happened to me, it was lack of ram.

It may not be your case, but how much ram do you have on your computer?

---

### Post by Dave85 on 2007-09-28
If my memory serves me right, it should be 1 Gb. So that should be plently.

---

### Post by dgtldaydrmr on 2007-09-28
Depending on what hardware you have...

You may want to try a alt-install CD as my new computers have alot of strange issues with live CD's 
also if you have sata it will be sda rather then hda.

On my new laptop hda is my cd/dvd writer and sda and sdb are my hard disks.
I think it regards them as scsi disks.

I know this isn't very useful information but just trying to help.

what issues with 7.04 are you having that you you feel the need to reinstall?

---

### Post by randytuggle on 2007-09-28
what happened to the computer that made you want to do a re-install in the first place? have you tried using a windows install cd on it? I sometimes use a winxp cd and install winxp, then do ubuntu as a second partition.

---

### Post by Dave85 on 2007-09-28
I orginally had ubuntu installed on the machine. I had installed Tomcat on it as im using it as a server for my wiki (among other things), then tomcat seemed to cease working. I spent a couple of weeks trying to figure out the reason.
Then yesterday, i noticed i could update ubuntu to 7.04. So i did just that hoping that could fix the problem.
When it was finished, I booted it up and it frooze (repeated a few times, each time it frooze).
So I decided to reinstall ubuntu from my CD. Now, It freezes after the intial loading and installing (freezes on a pale screen - same colour as the background on the desktop).
So now i can't boot up ubuntu, nor can I reinstall it.

---

### Post by randytuggle on 2007-09-28
try this: insert the ubuntu CD, when you see the "dos looking" GRUB menu come on screen with the "3 second countdown", hit escape. choose from the choices on screen by highlighting a RECOVERY mode of your choice and hit enter. This may fix your problem.

---

### Post by Dave85 on 2007-09-28
I got my wires crossed slightly. I'm not sure if this makes a difference but...
The original ubuntu on my computer was 6.10 - I then updated it through the online updates to 7.04. Now that was when the problem occurred. The CD I’m trying to reinstall ubuntu from is 7.04. 
Could 7.04 be the problem? Is there a known issue with this version?

Not sure if that helps?

---

### Post by Dave85 on 2007-09-28
I hit Esc and Bios came up! Will the Recovery section be under there? as i cannot see this option.

Also going back to a previous post, my hard-drive is SATA.

---

### Post by randytuggle on 2007-09-28
you have to hit escape after you restart and the initial startup screen disappears. It will be a black screen with a DOS looking menu in the upper left corner...
I had an incident this week very similar to yours. I WAS using Gutsy 7.10 successfully and tried a reinstall, then the CD wouldn't work when trying to use it once again. I would try to restart the computer, hit escape when GRUB appears, choose the oldest version of recovery you can choose (bottom of the lists). If that doesn't work, get your hands on a 6.10 CD for your pc (32 or 64 bit, not sure which you need).

---

### Post by Niniel on 2007-09-28
Why don't you boot DOS or a Windoze installation disk, if you have one, and use their fdisk to reset your hd, and only then try another install of Ubuntu? Do you have unrecoverable data on there?

---

### Post by tech9 on 2007-09-28
> **Dave85 said:**
> Hi,

After installing Ubuntu 7.04 and it not working probally, i decided to go back and reinstall my orginal copy of Ubuntu.
Only problem is, it's not installing properly. The bias is boot from the CD, and it comes up with the options to start or install ubuntu. Now, when i select this, it seems to start doing things. after about a minute, it comes up with a plale screen and doesn't do anything. Any ideas whats going on? And why the CD doesnt seem to install ubuntu even though its the same CD i orignally installed from.
Any help will be greatly appricated

Regards

-Dave

check the liveCD - detect for errors... you may need to create another CD

---

### Post by randytuggle on 2007-09-28
I think trying a Windows installer to format the disk is your best bet if all else fails,too.

---

### Post by tech9 on 2007-09-28
> **Niniel said:**
> Why don't you boot DOS or a Windoze installation disk, if you have one, and use their fdisk to reset your hd, and only then try another install of Ubuntu? Do you have unrecoverable data on there?

If you need to format the HD, just reinstall the OS and setup the partitions manually, check the format box - that will do it "on the fly" for you.

---

### Post by randytuggle on 2007-09-28
what brand of ubuntu-pre-configured pc is this? does it have a recovery function?

---

### Post by Dave85 on 2007-09-28
I can't seem to find the correct place to hit Esc, i dont see a 'DOS looking' section...
The motherboard is foxconn if that helps.

I may have to try the windows format way. But i thought that when you are booting ubuntu from CD, its only looking at the CD so would it matter what is on the hard-drive at the current time?
So would it be a motherboard or device driver issue?

---

### Post by randytuggle on 2007-09-28
something sounds screwy to me. If you have ubuntu on the drive, the grub menu should appear at system startup (have you tried shutting completely down and restarting t to look for the grub menu?). I'd just try a windows install. If windows installs, then try ubuntu with a 6.10 CD.

---

### Post by Dave85 on 2007-09-28
Maybe the pc starts too quickly for me to see the grub menu? Am i right in thinking this is on the startup and you have to hit Esc at the right time, or is it an menu that appears that you have no choice but to select something? lIke when you are giving the choice to 'Start or Install ubuntu' and other things?

I have just found my ubuntu 6.10 verson and tried installing that. Same problem :(

---

### Post by Dave85 on 2007-09-28
oh wait, my mistake, 6.10 did work! so there must be something wrong with 7.04 with my configuration?

---

### Post by randytuggle on 2007-09-28
Thank goodness for 6.10!!!!!!!! Let us know how it works when you get it installed.

---

### Post by Dave85 on 2007-09-28
Will do, and thanks for your help :)

Do you know of any known issues with the 7.04 version?

---

### Post by randytuggle on 2007-09-28
you're welcome!

---

