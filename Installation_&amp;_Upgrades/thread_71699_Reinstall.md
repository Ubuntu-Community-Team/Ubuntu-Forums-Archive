---
title: "Reinstall"
date: 2005-10-04
forum: Installation &amp; Upgrades
---

### Post by iAlta on 2005-10-04
Can I reinstall Ubuntu without loosing any data???

---

### Post by darkmatter on 2005-10-04
[QUOTE=iAlta]Can I reinstall Ubuntu without loosing any data???[/QUOTE]

Do you have a seperate /home partition?

---

### Post by iAlta on 2005-10-04
[QUOTE=darkmatter]Do you have a seperate /home partition?[/QUOTE]
I have no idea what you are blabbing about
If it helps, I have one /home folder.

---

### Post by dbott67 on 2005-10-04
[QUOTE=iAlta]I have no idea what you are blabbing about
If it helps, I have one /home folder.[/QUOTE]

What DarkMatter is talking about is a separate partition for your** /home **directory.  Linux allows you to create a separate partition for your data so that you can re-install without affecting the data in your /home partition.

If you did not specifically create a separate partition for **/home**, then you should backup your data to cd/dvd/usb/ftp/etc.

-Dave

---

### Post by dbott67 on 2005-10-04
Incidently, while you're backing up, if you had to make any tweaks to your **/etc/X11/ org.conf** file (X11 video configuration), your sound, network (**/etc/network/inerfaces**) or any other configuration files, it would be wise to back those up as well.

Then, after re-installation, you can just **sudo cp** them back to their original location and you'll be up & running quickly.

-Dave

---

### Post by dbott67 on 2005-10-04
[QUOTE=dbott67]Linux allows you to create a separate partition for your data so that you can re-install without affecting the data in your /home partition.
-Dave[/QUOTE]

By the way, you can also do this with Windows XP Pro (not sure about Home version).  You could create a FAT32 partition & mount it in your "Documents & Settings" folder so that you could have access to it in Windows & Linux if you're dual-booting.

Normally, people just add a 2nd hard drive & put their data on the new drive letter (i.e. F: ), however, you can just mount it in C:\Documents and Settings\username\My Documents\ and then it would appear to just be part of your C: drive.

Okay... I'll shut up now! :)

-Dave

---

### Post by iAlta on 2005-10-04
hehe.
lots of words I dont understand. but that harddrive-thing you mentiond. we hava 2 spare. they arent large, a dvd would be better, but you need a dvddrev for that. I will remove all files i dont need, have 2 of or are on a cd, comprimize the rest, install the bigger harddriv and reinstall ubuntu. simple.

---

### Post by iAlta on 2005-10-06
Just one more obstilcle...
How the f*** do I reinstall Ubuntu??
I have tried just about everything exept the right thing.
I have the install CD in but when i turn on the PC, it just reboots. When I installed Ubuntu the first time I got an option, boot from harddrive and boot from CD.

---

### Post by darkmatter on 2005-10-06
You need to set your computers BIOS to boot from the CD.

Press 'Delete' or 'Esc' before the bootloader kicks in to enter the BIOS. You should have an option to change the order in which your system accesses the bootable devices (CD-ROM, Hard Drive, Floppy)

Set the order so that the first bootable device is your CD-ROM. Insert the Ubunt CD in the drive and reboot.

---

### Post by iAlta on 2005-10-09
It's wery compicated, I can't really explain.

I have reinstalld now, but I can't... I dont know, it just doesn't work.

I turn on the PC, it boots, I have to enter my username and password, then it says I have 2 new messages, it says magnus@ubuntu &, and I type: mail, and the messeges come up, they say something like welcome to Ubuntu, this will guide you thrue setting up time, and bla bla bla. But then I come to magnus@ubuntu & again. what do I have to do??? 
I can't start ubuntu, all I can se is black and with, I'm getting insane.
Please help.

---

### Post by darkmatter on 2005-10-09
Hmmm... It should have taken you directly to a graphical login.

After you log in, and it shows you magnus@ubuntu, type the following

```
startx
```

And tell me what happens, does the GUI start, or do you get any errors?

---

### Post by iAlta on 2005-10-09
This is what it sais:
magnus@ubuntu:~$ stertx
- bash: stertx: command not found

---

### Post by iAlta on 2005-10-09
no wait it sais startx, bouth times

---

### Post by darkmatter on 2005-10-09
Hmmm... Looks like something is missing there. 

login again, and type the following 
```
sudo apt-get install ubuntu-desktop
```

You will be prompted for your user password. That should fetch and install everything you need (If the problem is what I believe).

After the install, you may to reboot your system. After you log in again, enter the command
```
sudo dpkg-reconfigure xserver-xorg
```

You will be guided through the configuration of x

when it is finished, type 
```
startx
```

or simply reboot.
Either way, you should be greeted with a graphical login.

Good Luck

---

### Post by iAlta on 2005-10-10
Thank you so much darkmatter, if you ware here I would kiss you. Man, it finaly worked. 
Well, I didn't reboot between thoese codes, and I didn't come into a grafical login, I came right to the desktop. But when I rebooted again, to see if it worked I came to the grafical login screen.

---

### Post by darkmatter on 2005-10-10
[QUOTE=iAlta]Thank you so much darkmatter, if you ware here I would kiss you. Man, it finaly worked. 
Well, I didn't reboot between thoese codes, and I didn't come into a grafical login, I came right to the desktop. But when I rebooted again, to see if it worked I came to the grafical login screen.[/QUOTE]

LOL. Your welcome (though my wife may have something to say about that):D 

The startx command will always bypass GDM (GNOME Display Manager - the login screen) and takes you directly to the desktop, as you are already logged in when you issue the command. And, of course, you we're never required to reboot. That was why I said that you MAY reboot.

I was a Windows user once, and it seems that many expect a reboot, so I always give them that option. It's kinda' like comfort food...

I'm glad I was of help, iAlta.

Welcome to the Ubuntu Forums.

---

### Post by Raj on 2005-10-10
Hi all,

The timing of this particular thread is amazing. Here goes [darkmatter, I am hoping you are going to be my champion here!! :)]

P3-800/128Mb/Hoary

Install was great. Up and running [after major problems with speedtouch 330 ubn modem] about 3 weeks ago. Decided was so happy with it, killed XP [finally].

Since I think i am a little techie in windows, I go and play. install all sorts of WM's/DE's and playing around hacing fun. nice and customised, automounts etc etc. then yesterday i was looking through the index of HOWOT's and found a string of good ones to update firefox to alpha 1/openoffice 2/wine/DC++ etc...

so off I go [dont remember the order]. one of the HOWTO's [could have been the openopffice2 one] seemingly updated my repository list [something like extracting the deb files to a local folder and then adding the extracted files to a self-created Repository folder in my home directory and then pointing the repo's to it - please bear in mind i am completely working off memory here].

anyway - here is the substantive problem. somehow it seems [mr n00b diagnosis here] that it added the Breezy [or at least some Breezy] repo's to my list. Ubuntu tells me there are update, around 200Mb of them. I think this is a little strange, but since i want all the latest update, off we go and download and install.

of couse now the desktop manager crashed and when it drops out to the consol, i notice that rather than it stating it is hoary etc etc, it is saying that the system is ubuntu breezy and wont load X [tried startx - but no go]. did give me a couple of commands to tyr [apt-get commands] but they didnt work.

so i think i have "upgraded" many of the system files to breezy, resulting in a mixed [and fubar-ed] system :(

ok, well this *might* have been ok, except i am unable to get online [even in text mode now - although this im a little certain about, as i tried to ping a few sites with no luck, so im thinking thats out]. i luckily [?] had a spare partition [hda1] so i try to install hoary on that. VERY wierd installation process, i think it must have been looking at the current install, but it saw an install of "breezy" and added it to grub. so i still have the old system, with a new one.

questions i have are:

1. possible to recover the original system? if so, how...please?!?!
2. i dont have a separate /home partition so is it possible to move the /home dir from the original install to the new install? if so how? bear in mind that the folders of the users, except for the guest account are password locked. will this be a problem
3. can i transfer all of the settings over? ie monitor/modem/fstab/etc settings? if i can, how will this affect the new system when it tries to use these settings and for example, an app which i installed via apt-get before is not on the "new" system? same with upgrade etc? wont this corrupt the system?
4. if i am not online, the problem is going to be getting on line again, so i can get help from you guys and also start the upgrade/customise process again. any ideas?

i know this has been a long email, but people in forums seem to be more helpful with more detail. also, any idea as to how this could have happened and how to stop it in the future.

if i am able to do all of this, any advice [i have looked at howtos and many threads on backups etc, but i am not very technically savvy and therefore am asking independtly] on how i should set up the drive etc? breakdown is

/had1 = 5gb = "new" install
/hda5 = 5gb = "old" corrupt install
/hda6 = 250mb = swap
/hda7 = 63gb (? approx) = fat32 = data

thanks heaps in advance

raj

---

