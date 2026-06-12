---
title: "ubuntu 10.10 boot from portable hard drive/ grub issue"
date: 2011-04-17
forum: Installation &amp; Upgrades
---

### Post by jacob.harris9799 on 2011-04-17
Hey guys!

I'm a week into using ubuntu and i've hit several roadblocks.. I am running vista and U10.10 on a compaq CQ60, and ive been having the wireless hardware button issues. but thats beside the point

Somehow my ubuntu partition decided to erase itself. so today i go through the steps to boot from my portable hard drive, and install it again. I follow the steps to the T. change the boot order so it will boot from the phd.. choose boot ubuntu.

then it loads grub... it has done this since friday (it is now sunday). I am not experienced with grub or any command line stuff at all, other than i get how to type it in, lol.

any help is greatly appreciated!!! ( i have a paper due wednesday!!!)

sidenote: due to unknown reasons, my computer will not write cd's, so I have to use the usb method. 

thanks so much!

---

### Post by Dutch70 on 2011-04-17
Hi and welcome to UF

 It's not clear at all what you're problem is, therefore helping you solve it is even more difficult. Ubuntu partitions don't erase themselves.

> then it loads grub... it has done this since friday 

Are you saying it's been loading grub since Friday?

Remember...we're not there looking at your computer. The more clear you make things, the more likely you are to get help. Every sentence you type, ask yourself..."how might this be perceived incorrectly?"

---

### Post by jacob.harris9799 on 2011-04-17
Sorry about the confusion!

at the dual boot screen, when i choose ubuntu.

it displays something in the top left corner of the screen, something about NTFS, but it is so quick i cant catch it all.

immedieately after that it opens a screen that says GNU GRUB (version number)

it has a short bit about "minimal BASH- like command line editing"

then for the command line it has 




grub>

any thing i can do to give more info?


and yes, it has been going through this process since friday. windows loads normally.

---

### Post by Dutch70 on 2011-04-17
I totally understand. Asking a support question is more difficult than answering one for sure.

So you were getting this error, then you reinstalled Ubuntu & you're getting the same error? 

Lets have a look at your boot info script.

To post your boot info script, boot up to your live cd/usb,  download the boot info script from the following link & save it to your desktop. 
[COLOR="RoyalBlue"][[COLOR="RoyalBlue"]http://bootinfoscript.sourceforge.net/[/COLOR]]("http://bootinfoscript.sourceforge.net/")[/COLOR]

Then open a terminal (Cntrl+Alt+T) and run the following command...
```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a results.txt file on your desktop. Open that file and copy/paste the info  **between code tags** using the "#" symbol in the toolbar of your next post.

To put it between code tags, just click the # symbol in the toolbar & paste it between [CODE] [ /CODE] tags. Do not skip this step, it needs to be done to keep the formatting.

---

### Post by jacob.harris9799 on 2011-04-17
Due to misplacement of the original,:rolleyes: i am burning a new boot cd. as soon as i get that done, i will have the info you need!

again, thanks so much!

---

### Post by jacob.harris9799 on 2011-04-17
ok, I am confused now. Download a new iso for 10.10, followed Ubuntu's directions to make a new cd, and i have a new issue. it begins to boot like normal, then says "cannot mount cdrom/......" what am i doing wrong?

maybe to clear things up, i cant get ubuntu to boot. Stupid question, but how do i run that code?

i took the cd out, rebooted ubuntu, and it took me right back to GRUB. I tried to run the code there, to no success. sudo was not recognized, nor was bash. 

as you can see, i am clueless.

---

### Post by jacob.harris9799 on 2011-04-17
ok, when i boot from the cd, this is what it gives me:

```
BusyBox v1.15.3 (ubuntu version) builtin shell (ash)
Enter "help" for commands

(Initramfs)mount: mounting? Dev/loop0 on //filesystem.squashfs failed :input/output error

Can not mount /dev/loop0 (/cdrom/casper/filesystem.squashfs) on //filesystem.squashfs
```



open call for anyone to help! it would be greatly appreciated!!!

---

### Post by jacob.harris9799 on 2011-04-17
> **Nicolasa77 said:**
>  I will contact with you right now. Thanks for sharing.

just helping others by helping myself! haha:lolflag:

---

### Post by Dutch70 on 2011-04-17
If you can't boot from the cd you created, you may want to check the md5sum of the downloaded .iso.
[[COLOR="RoyalBlue"]HowToMD5SUM[/COLOR]]("https://help.ubuntu.com/community/HowToMD5SUM")
Check the cd for defects. Did you burn it at the slowest speed possible?
[[COLOR="RoyalBlue"]CDIntegrityCheck[/COLOR]]("https://help.ubuntu.com/community/Installation/CDIntegrityCheck?action=show&redirect=CDIntegrityCheck")

If you have a usb stick that you can use, it's much easier & faster.
[[COLOR="RoyalBlue"]Using UNetbootin to create a Live Linux USB[/COLOR]]("http://www.pendrivelinux.com/using-unetbootin-to-create-a-live-usb-linux/")

---

### Post by jacob.harris9799 on 2011-04-17
I checked the md5sum. they are the same. where do i go from here?

in the mean time, i will try to burn a new cd at the slowest speed possible. should i use the same iso file?

---

### Post by Dutch70 on 2011-04-17
No, you will have to download a new .iso.

Hey, what happened to the spammer? lol

---

### Post by jacob.harris9799 on 2011-04-17
> **Dutch70 said:**
> No, you will have to download a new .iso.

wait, so if they DO match, i still need a new one? or did you post this before i realized i had selected the wrong .iso? haha. stupid me.

> Hey, what happened to the spammer? lol


methinks he got caught!!! dumb people, we dont need no mo dumb people on this green earth!

---

### Post by jacob.harris9799 on 2011-04-17
ok, with the correct .iso on a new cd, i tried to boot it up... no dice )*&%)&*^%$*^%#&%$#@&%$@# ugh! haha.

it just takes me to that darn grub interface.

---

### Post by Dutch70 on 2011-04-17
I don't know where we got mixed up, but the md5sum's have to match exactly. Then you have to check the cd for defects. If both of these check out, it should boot.

And yeah, I reported the spammer. :D

---

### Post by jacob.harris9799 on 2011-04-17
nice job! :p will reboot now.

---

### Post by jacob.harris9799 on 2011-04-17
im not rebooting right.

turn on, hit escape, then select cd as boot device, hold a button down, still takes me to the dual boot screen. so i select ubuntu. hit enter, hold a button, then right into the GNU GRUB screen.

---

### Post by Dutch70 on 2011-04-17
What program are you using to burn the cd? I don't know which ones, but some burning programs do not work well. I think I'd try that external usb. It's going to be labeled sda or sdb or something like that, just DO NOT make the mistake of putting it on the wrong one. Which would obviously clean out windows.

Are you positive the md5sum matched up perfectly?

What did you use to install it with the first time?

---

### Post by jacob.harris9799 on 2011-04-18
ive just been using windows native drag and drop.

here what i dont understand, i have downloaded 3 different .iso's, and the md5's are all differetn. im hitting the same link on the ubuntu website.

im starting to get peeved at my lack of problem-solving prowess tonight.

---

### Post by jacob.harris9799 on 2011-04-18
this is the correct hash > 59d15a16ce90c8ee97fa7c211b7673a8
ubuntu-10.10-desktop-i386.iso


here is what i have on the newest cd.
(which is what i thought i had already verified.)
> 3c522b01341cfd3d233c0866e10533fe

---

### Post by jacob.harris9799 on 2011-04-18
Question: when running [URL="https://help.ubuntu.com/community/BootFromCD"/URL] BootFromCD
it does not improve anything. 

Dutch70, nothing is working.

i wouldnt mind trying the external, but its got ~100 gig of valuable stuff, and what ive read says the process can be tricky. but if i could find a very detailed how-to, i would definitely try it. ive got to figure something out.

---

### Post by Dutch70 on 2011-04-18
> **jacob.harris9799 said:**
> this is the correct hash 

here is what i have on the newest cd.
(which is what i thought i had already verified.)

"on" the cd??? It's the .iso that you want to verify.
Again, how did you install it the first time?

You may also want to try a cd from a different batch if possible.

---

### Post by jacob.harris9799 on 2011-04-18
somehow, using the same link, i downloaded 2 different .iso's. 
the first was like "59d... or something" which is the one i verified for md5. the second was "3c.." which somehow was the one that i wrote to the cd. 
 
> You may also want to try a cd from a different batch if possible 
 
what do you mean from a new batch?

---

### Post by Dutch70 on 2011-04-18
From a different group or bundle of cd's that you've bought. Maybe a different brand. You also may want to consider purchasing a usb stick, you can get a 2GB usb stick cheap these days.

You need to make sure you have 1 downloaded .iso and verify that the md5sum matches perfectly, delete any others.

---

### Post by jacob.harris9799 on 2011-04-18
deleting all .iso's now. will download a new one. then try on another cd. while it is downloading to the cd, im gonna take out a search warrant for the usb i used originally

---

### Post by jacob.harris9799 on 2011-04-18
QUESTION!!!!


downloaded the i386 iso.

using wubi, it downloaded the lucid-desktop-amd64.iso

is this ok?

by the way, when i get this all straightened out, i will create a new topic that hass all the info in one nice, neat post.

---

### Post by jacob.harris9799 on 2011-04-18
Using the usb method, i got ubuntu to work

[B]SUCCESSSSSSSSSS!!!!!!


THANK YOOOUUUU DUTCH70!!![/B]


it would be fantastic, but.......


i still have the hp/wireless button/hardware interface malfunction.... any ideas? anyone? calling anyone on earth!

---

### Post by Dutch70 on 2011-04-19
Great! Glad to hear you got it going. :D
and you're welcome!

I wouldn't worry about starting a thread to put all the info about this problem in one place, just mark this thread solved, see my sig for how to.

You may want to start a thread for your new problem if you cant find anything with a google search. A lot of times that's faster & someone has had the same problem before, you can bank on it.

---

### Post by jacob.harris9799 on 2011-04-19
I searched for hours yesterday, but I coudlnt find a way that I understood.  a lot of people have the same problem, but I do not have access to an ethernet connection. I do have wireless through windows, and today I got another usb stick. But I haven't seen a way to fix it through that..

---

