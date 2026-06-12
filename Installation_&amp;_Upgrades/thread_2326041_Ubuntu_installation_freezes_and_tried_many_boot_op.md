---
title: "Ubuntu installation freezes and tried many boot options (DRIVING ME INSANE)"
date: 2016-05-27
forum: Installation &amp; Upgrades
---

### Post by mario71 on 2016-05-27
Hello there users ,

Im trying to install Ubuntu 15.1 on my Dell netbook .

This happens with 16.04 ,15.10 and 14.04 .

I don't quite remember how I installed 15.04 but i remember i installed a 15 version so :
I have successfully used Ubuntu 15.04 and was very happy with it until it i tried to upgrade to 15.10 and my Login screen freezed (not after login in but before) so i tried many 
different things until I decided to do a clean install which freezes while loading the desktop if no options are set.

Here :

[ATTACH=CONFIG]269331[/ATTACH][ATTACH=CONFIG]269332[/ATTACH]

If I try noacpi or acpi=off I have the same problem except the battery icon doesn't appear.

If i try any other options like:

nomodeset
nolapic
noapic
video=1024x600-24@60 
video=VGA-1:1024x600-24@60
pci=nomsi

and others it just freezes on a black screen.

I believe its a video issue but i have tried many options 

Currently i have 14.04 after upgrading form 12.04 because the only version I'm able to install is 12.04 .

I have already checked the md5sum , tried different USB drives , tired with rufus , the built in disk creator from Ubuntu 16.04 (on my other laptop) , unebootin , universal USB disk creator.

I booted the USB on my other laptop as well and the installation seems to load fine.



I know that after the start lightdm command its where it freezes entirely also this new Sony USB flash I'm using come with an access indicator LED which stops blinking so I'm entirely sure it freezes.
Waited for about 1.5 Hours.

Any suggestions or help with the debugging of this ?
Like creating a file with the log on the USB maybe and save the log to know what exactly happens with the last thing it tries to load.

---

### Post by Omar_Jair on 2016-05-27
You should probabbly try with a live CD or a "apt-get dist-upgrade"

---

### Post by mario71 on 2016-05-28
Thanks for hte reply
What do you mean by a live CD?

I 've already tried upgrading from 14.04 to 15.10 for about 3 or 4 times ,it always fails.

---

### Post by gordintoronto on 2016-05-29
How much memory? Disk space? What CPU? I assume your netbook does not have an optical drive, and you boot from USB to attempt to install?

In most cases, nomodeset gets past video issues.

Have you tried Xubuntu 16.04? I have installed it successfully on several dreadful computers.

---

### Post by Omar_Jair on 2016-05-29
When you go to Ubuntu's webpace they let you download a .iso image, it lets you to try ubuntu without installing and also lets you to install it rigt away, also check your HDD space, memory and swap.

---

### Post by mario71 on 2016-05-30
Thanks i will give it a try to Xubuntu since i have been struggling with Lubuntu and Ubuntu ,I cant install Ubuntu and Lubuntu only works after the install if I reboot it wont start .

I have :

Intel Atom N450 1.66 GHz
1 GB RAM
250 GB HDD 
No optical drive as you mentioned

I dual boot with Windows XP

When I said that I didnt remember how I installed it was because I dwonloaded a non realased version i think but yeah i now know why you mentioned a live CD and thats why I downloaded Ubuntu 15.1 and boot from my USB since i dont have a dvd drive but I stronlgy think isnt a USB boot issue but a problem with the fact that the video drivers arent too compatible with my netbook since i can install Ubuntu 12.10 from an SD card :O so in any case i get an external DVD drive I dont think that's gonna help :(

---

### Post by mörgæs on 2016-06-01
How did Xubuntu 16.04 work?

---

