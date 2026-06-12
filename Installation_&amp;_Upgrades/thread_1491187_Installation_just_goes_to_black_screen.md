---
title: "Installation just goes to black screen"
date: 2010-05-23
forum: Installation &amp; Upgrades
---

### Post by Frustrated Noob on 2010-05-23
Hey guys, i have spent hours trying to get Ubuntu to run trying multiple programs for multiple burnt cds in both of my computers cd and dvd drives using several parameters and i still cannot get to the welcome screen. I will see the little thing at the bottom of the screen (which i learned i have to press enter for to get to the next step) but after selecting install i just get a black screen that lasts for hours (left it on overnight). I have looked all over Ubuntu support for different theories and alternate installation methods but i feel like im going on a scavenger hunt. If any of you can help, it would be much appreciated.

---

### Post by wojox on 2010-05-23
When you get to the options screen press F6 and check **nomodeset**

---

### Post by howefield on 2010-05-23
When booting, try pressing F6 after selecting your language, and select the nomodeset option. Then continue booting, if that doesn't work, press the Esc key after pressing F6 as above, and remove "quiet splash--" from the end of the boot line.

---

### Post by Rubi1200 on 2010-05-23
You can try this:

[http://ubuntuforums.org/showpost.php?p=9239795&postcount=19](http://ubuntuforums.org/showpost.php?p=9239795&postcount=19)

Hope it helps.

---

### Post by darkod on 2010-05-23
> **Rubi1200 said:**
> You can try this:

[http://ubuntuforums.org/showpost.php?p=9239795&postcount=19](http://ubuntuforums.org/showpost.php?p=9239795&postcount=19)

Hope it helps.

If this works you should be able to make it permanent in /etc/default/grub

Also, you might not even need it as permanent fix. Only to boot into live mode to install, and then to boot the installed system the first time. Once you have booted it, it might locate new drivers and install them, provided this issue is due to drivers. So you might not need it as permanent fix, but if you do, parameters are set in /etc/default/grub

---

### Post by Frustrated Noob on 2010-05-23
Wow you guys responded fast! thanks for the suggestions, nomodeset worked (the only parameter i didnt try of course)

however, i got to 25% of the download and i got input/output error. i believe it said ernor 5 or something like that. it said i will go to the desktop or something to fix the problem. i am currently on a black screen and to avoid pressing anything im on my dsi`s internet. now what? :/

---

### Post by darkod on 2010-05-23
> **Frustrated Noob said:**
> 
however, i got to 25% of the download and i got input/output error. 

What download are you talking about?

---

### Post by steveneddy on 2010-05-23
25% of the DOWNLOAD? 

Are you downloading the software or installing an OS?

also, are you using wubi?

---

### Post by Frustrated Noob on 2010-05-23
i apologize. i believe i am downloading the os. ive gotten past welcome screen time zone and was on the guided tour while it was installing. 

the error screen suggested cleaning the disk, cleaning the drive, or slowing down the burning speed

---

### Post by Frustrated Noob on 2010-05-23
> **steveneddy said:**
> 25% of the DOWNLOAD? 

Are you downloading the software or installing an OS?

also, are you using wubi?

i think im using wubi, but im not sure. are you able to tell from my last post? 
i know whenever i was on winows and i would insert the cd that would come up on autoplay

---

### Post by darkod on 2010-05-23
> **Frustrated Noob said:**
> i apologize. i believe i am downloading the os. ive gotten past welcome screen time zone and was on the guided tour while it was installing. 

the error screen suggested cleaning the disk, cleaning the drive, or slowing down the burning speed

Not I am confused even further. I thought you were installing ubuntu from a cd that you have already burned from downloaded image??? You said you used different CDs in your first post.

And if wubi is what you are talking about, then nomodeset has nothing to do with it. It doesn't work the same as full install.

---

### Post by darkod on 2010-05-23
> **Frustrated Noob said:**
> i think im using wubi, but im not sure. are you able to tell from my last post? 
i know whenever i was on winows and i would insert the cd that would come up on autoplay

Don't boot windows. Have the cd in the computer, restart and boot from the cd. In BIOS the cd-rom needs to be before hdd in the list of devices so you boot from the ubuntu cd.

Don't install it from inside windows.

---

### Post by Frustrated Noob on 2010-05-23
> **darkod said:**
> Don't boot windows. Have the cd in the computer, restart and boot from the cd. In BIOS the cd-rom needs to be before hdd in the list of devices so you boot from the ubuntu cd.

Don't install it from inside windows.

dont worry thats what ive been doing. when the computer is booting go to boot menu and boot from the cd drive. i did that and got as far into the process as installing ubuntu over my computers hard drive and 25% of the download until the error popped up. 

im sorry for the confusion. obviously im confused too. 

and about the multi cd thing. i just used several cds in the process of getting this far. they didnt work until this one bc the iso image was on the cd but not all of the files

i also have 2 cd drives to add to your confysement. my bad for icluding that

---

### Post by howefield on 2010-05-23
> **Frustrated Noob said:**
> ... 25% of the download until the error popped up.

Sounds like you are in the installation process, 25% of the way into the installation when you get the error. You are not downloading here.

Did you check the file you downloaded against the MD5SUM hash to verify the integrity of the downloaded iso, and also of the burned CD ?

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by houseworkshy on 2010-05-23
I've seen many posts which conclude that re-writable cd/dvd's are not suitable for system discs so it could be as simple as using a writeable once only disc burnt at the lowest speed available after checking the integrity of the iso image with the checksum.

---

### Post by Frustrated Noob on 2010-05-23
Using houseworkshy and howe's advice i went over to my grandparents house and am using a different type of disk with a different burner and im going to see how that works. I will post after i have tried that, thanks everyone for the help so far i didnt think there would be people at all times ready to help out idiots like me :P

---

### Post by Rubi1200 on 2010-05-23
Here are some other links that you may find useful for general advice etc:

[http://ohioloco.ubuntuforums.org/showthread.php?t=801404](http://ohioloco.ubuntuforums.org/showthread.php?t=801404)

[https://help.ubuntu.com/10.04/index.html](https://help.ubuntu.com/10.04/index.html)

---

### Post by Frustrated Noob on 2010-05-23
it worked! the installation finished.

however after restarting like it told me to upon booting my monitor says no signal and goes black like when i started. my computer hates me

---

### Post by darkod on 2010-05-23
> **Frustrated Noob said:**
> it worked! the installation finished.

however after restarting like it told me to upon booting my monitor says no signal and goes black like when i started. my computer hates me

Did you have to use nomodeset or any other parameter to make the installation start?

---

### Post by Frustrated Noob on 2010-05-23
i backspaced quiet splash and used nomodeset

---

### Post by darkod on 2010-05-23
> **Frustrated Noob said:**
> i backspaced quiet splash and used nomodeset

You need to read our replies more carefully. :) I already said if you need specific parameters to boot live mode and install, you'll have to do the same at first boot.

When the grub menu shows, highlight the ubuntu entry but don't hit Enter. Hit 'e' instead. That will show you the boot commands. Use the arrows keys and End to go to the end of the linux line.
Add nomodeset at the end. Press Ctrl + X to boot.

If that worked, see if ubuntu will find any new drivers and install them. If it does, reboot to see if the problem is fixed.

If it's not fixed even after new drivers are installed, use the same procedure to boot the ubuntu entry and post here, I will show you how to add nomodeset permanently.

---

### Post by Frustrated Noob on 2010-05-23
:( 

i am sooo sorry for this but how do i get into the grub menu? i would have tried to figure that out myself on the internet but my dsi is like using something worse than ie

---

### Post by darkod on 2010-05-23
> **Frustrated Noob said:**
> :( 

i am sooo sorry for this but how do i get into the grub menu? i would have tried to figure that out myself on the internet but my dsi is like using something worse than ie

No problem. The boot menu is shown only if you have more than one OS. If you have only ubuntu it won't.

In that case you need to press Shift but before it starts to load ubuntu. Then it will show you the grub menu.

After the BIOS POST finishes, just start hitting Shift.

---

### Post by Frustrated Noob on 2010-05-23
when i do that i get the option to load boot graphics y/n 
then to detect dsiplay size y/n. after doing those i get a bunch of numbers and cant type anything only hit a key to enter. fml

---

