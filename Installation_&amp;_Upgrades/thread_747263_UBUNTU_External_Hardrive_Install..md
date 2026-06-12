---
title: "UBUNTU External Hardrive Install."
date: 2008-04-06
forum: Installation &amp; Upgrades
---

### Post by oligray on 2008-04-06
[SIZE="5"]Installing to External Hard Drive[/SIZE]

Installing to an external drive isn't as easy as it sounds unless you know what to do, you can try it without this guide and you'll probably get grub error 17.

If after following this guide properly you still have issues im sure WE can try and figure them out. also tell me where i can improve this guide as i mention below i made this for myself originally so it can be improved for others to use.

This is an edited version of gpmatinsons ([http://ubuntuforums.org/showthread.php?t=678146](http://ubuntuforums.org/showthread.php?t=678146)) guide, which i originally made for myself to make it easier for me to follow quickly. I deleted some of the unnecessary bits which you don't need to know and edited various other bits but not greatly at all so thanks.

Here's the process. 

Firstly you need to make sure you have boot order as : (to do this you need to enter the Bios setting usually by hitting f2 just after you have turned your computer on)
1 Cd
2USB
3Internal Drive


You boot your live ubuntu cd then:


1. Install. Use the standard install app right on the desktop. You'll want to pay special attention 	to the Disk Selection and last screens. 
	In the Disk selection screen, choose manual. Here' make sure that you are selecting your USB 	drive to install too. There will be some text describing the drive. Make certain that you are 	installing to your external drive. Chose manual if your not going to be using your whole 	external drive. 
	Make sdb1 ext3 with a mount point of /    it should be over 3gb and if you've got space 10gb 	would be ideal. Make sdb2 a Linux swap format. Make sdb3 ext3 with a mount point of 	/media/sdb3. This can be as large as you want. If you want to have a partition for windows 	leave it empty and format it within windows.

On the last screen click on advanced and make sure you choose HD1 for your grub installation This is your USB drive. 

2. Open Terminal window... Applications > Accessories > Terminal. 

3. In the command prompt type "sudo mkdir /mnt/ubuntu"

4. type "sudo mount /dev/sdb1 /mnt/ubuntu"

5.Type "sudo mount -tproc proc /mnt/ubuntu/proc" 

6. type "chroot /mnt/ubuntu"  Your root level is now the USB drive and you are kind of using your new Ubuntu disk. 

7. type "su" to make yourself superuser. You are going to work on system files that require this access. 

8. type "nano /etc/initramfs-tools/modules"
and add the following lines to the end:
sd_mod
ehci-hcd
usb-storage
scsi_mod
sd_mod

Exit (Ctrl +x) then save (Y) then press Enter

This adds the support needed (but not initially available) to mount and run a USB hard drive in the initial ram disk,

9. I edit /etc/initramfs-tools/initramfs.conf ("nano /etc/initramfs-tools/initramfs.conf")to include a line at the top that reads:
"WAIT=4" in the front of the file. 
close and save this file. 
then I made the initial ramfs:

10. "mkinitramfs -o /boot/initrd-img."<hit tab and enter> /lib/modules/"<hit tab and enter>"

11. type &#8220;nano /boot/grub/menu.lst"
change all the hd1,0 to hd0,0 and vise versa.

You Have Successfully installed Ubuntu to your external Hardrive.

Reboot and set up your system..
[edit] 2 hours after making i thought i would tidy it up. [eidt] removing via guide.

---

### Post by oligray on 2008-04-06
Thanks for the thanks..

as i said this isnt really my work and it is a bit messy so you might prefer to look at the link at the top of the thread.. the original is quite a popular thread. i have often been pointed to it when ive been struggling with ext hdd. so they really deserve thanks. all i did was to keep the instructions and remove the jargon (at least some of it|). So if you prefer to know what happens when you type these commands into the terminal view his thread

---

### Post by oligray on 2008-04-06
another point i might forget to check this thread.. so if you have a problem post on the thread so other people can help but contact me via personal message.. however i am not a confessed expert on ubuntu to any extent. only really just started but im getting the ropes quite quickly i reckon..

---

### Post by oligray on 2008-04-06
and im only 15 so no big words i wont understand.. easier to save the embarassment ahah

---

### Post by oligray on 2008-04-07
i thought this was a good thread... i wish someone had made it like this for me when i was doing this... so if you read it comment on it please gets it going and makes it a known thread

---

### Post by aimpau on 2008-04-07
Can you make something about my situation?

How to install and dual boot xubuntu in a single hard drive with an XP SP2 installed?

---

### Post by oligray on 2008-04-07
i would have thought that would be quite easy...

tbh i am quit new to linux... so ive never touched my interal drive.. but i should think you just have to manually partition..

make am 3gb+ partition ext3 sda2 presuming windows is your first partition with mount point / 
make a partition the size of your ram for swap
then make one as big as you like for your media with a mount point of /media/sda4   
replace sda4 with whatever the location of that partition is if different 

then the rest of the install should be easy because the installer is made for internal drives. i dont think sual booting will be an issue at all grub will handle that.

thats your basic install most the info in my guide is very specific to external drive and doesnt matter if your using internall

however sayiung all that i dont know what the xubuntu installer is like.. im presuming its the same as ubuntu..

---

### Post by rugbylg6 on 2008-04-07
I just set up kubuntu from a disk I had last night, I was 7.04 (feisty). I followed the directions exactly (some difficulty with the code in terminal), and it seemed to work. Today I installed the 7.10 (gutsy) upgrade and when I restarted and tried to load I came up with the error 17. Do I have to start over or is there a fix for this? 
Thanks for your help, this is a great post.

---

### Post by rugbylg6 on 2008-04-07
aimpau,

You should be able to just start installation and move the partition using the slider (for an internal drive you don't need to go to advanced mode), when I set up my dual boot it was super easy and worked great the first time. 
Good luck

---

### Post by oligray on 2008-04-08
yeh aimpau that is right..

error 17 hmmm i remember that error..

is it possible to reinstall or will you be losing data you need.

did you change it to hd1 in the advanced bit because i think that is how you get the error.
alternatively you could try the supergrub disk but im not experienced witht that.. however i did save me last night.. lol
do a google search and get back with what error 17 means.. or can you not get onto winblows either

i remember haing that problem tho. i dont remember how to solve it tho..

i will do some searching aswell for you and get back to you on here to tell you how to fix it.

i really need to know more about your situation because all you might have to do is boot into windows and use a mbr fix program.. i will also get back on the details of that because i cant seem to find it on the web.

---

### Post by oligray on 2008-04-08
axtually dont bother google searching i dont think it will help you only confuse you more.. lol
i think when i had this issue it was a very different reason to everyone else

someone correct my last 2 posts..

tbh i suggest reinstalling or trying hardy heron. and installing that..

1.Use Super Grub disk and fiddle with that and see if you can get it working...
2.<use program for xp if i can find it>
3. Try a fresh install - this wont solve it if you instaled Grub to thw internal accidently.. so i actually suggest you do 1 or 2 then reisntall ubuntu.. 2 is easier if i can find it.

---

### Post by oligray on 2008-04-08
ok i couldnt find the program but try this [http://askbobrankin.com/fix_mbr.html](http://askbobrankin.com/fix_mbr.html)

---

### Post by rugbylg6 on 2008-04-08
I got it, thanks. In device.map you can change what the internal hard drive and what the external hard drives are called (hd1 or hd0). once you do that, in menu.lst you change any internal OS's to whatever you set the internal hard drive to (hd1 or hd0) then for any external OS's change it to whatever you set the external hard drive to.

---

### Post by oligray on 2008-04-08
yeh i knew that...

because that is basically what the last part of my guide is about so by the sounds of it you didnt follow tht properly lol.. did you edit menu.lst on install..

well im glad you got it all working :) 

i presumed you couldnt boot into ubuntu..lol

when ever ive had errors except for last night. ive only been able to get into winblows not ubuntu.. last night was opposite tho but tht was error21

---

### Post by rugbylg6 on 2008-04-08
yeah your right, that was my bad. Well thanks for the help this was great.

---

### Post by oligray on 2008-04-08
its alright i dont mind helpingg becuase so many people have helped me on here..

now i need a new pc which has a non VIA graphics card.. if your getting a pc to run ubuntu or any  linux on make suere it isnt VIA lol

i wanna get good at using linux so i can help people.. lol :)

---

### Post by oligray on 2008-04-09
if you use this guide...

please either give me or the original writer thanks whoever you feel more appropriate..

and reply with your personal experience... and problems... 

or if it just went well

---

### Post by oligray on 2008-04-17
Bump

---

### Post by amyst on 2008-04-18
Thanks for posting this tutorial. I plan to install ubuntu 7.10 on a 500 G Western Digital external usb drive, but before I do something stupid to my only laptop, can I ask: 

Do have the live CD install 7.10 onto the drive before "sudo mkdir /mnt/ubuntu", ... or after “nano /boot/grub/menu.lst", when I modify the menu.lst? 

Is it necessary to disassemble the internal hard drive of my laptop?

If any error might occur, will it make changes to mbr that can't be reversed without grub-level fixes? I am thinking that if something goes wrong, my last resort will be reinstall Ubuntu on my laptop. But from other posts, it sounds like mbr has its own memories that store grub information, and is independent of OS. I would very appreciate it if any one can explain what is stored on mbr, and what permanent changes this install will make to it.   

Thanks in advance!

---

### Post by oligray on 2008-05-06
Hi sorry i didnt reply... :S

ive got exams coming up.. GCSE

i do not unferdstand > 
Do have the live CD install 7.10 onto the drive before "sudo mkdir /mnt/ubuntu", ... or after &#8220;nano /boot/grub/menu.lst", when I modify the menu.lst?

it is on your external hardrive when you finish install the other bits are just to make it work (if that is what it means)

also is your laptop primarily windows. if so your windows mnr should not go wrong if you follow my guide properly.. however if it does and you cant access windows.. download super grub disk and use that to fix it.

thanks

i will try to offer more support when i get a new computer and am able to run ubuntu properly.

---

### Post by oligray on 2008-05-16
Bump

---

