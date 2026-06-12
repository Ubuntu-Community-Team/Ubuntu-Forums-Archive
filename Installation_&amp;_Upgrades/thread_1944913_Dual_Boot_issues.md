---
title: "Dual Boot issues"
date: 2012-03-22
forum: Installation &amp; Upgrades
---

### Post by Oswiu on 2012-03-22
Hi folks,
I hope someone can help with a boot issue I'm having. This is my first post and I'm still relatively new to ubuntu so please bear with me.
I've built a few dual boot PCs before, basically using the ubuntu downloader via USB pen to install onto various XP machines and it always presented me with XP boot manager, which I know how to configure.
 My friend asked me to rebuild her XP laptop and add ubuntu as a second option; she liked the look of it, but still needs the familiarity of XP to get work done as its her only machine. I installed a fresh copy of XP and then installed ubuntu expecting XP boot manager, but instead got GRUB 1.99.
Unfortunately I know nothing about GRUB configurations and it defaults to Ubuntu as main boot OS instead of XP. 

So my dilemma is this: 
I'd prefer to use XP boot manager first and for it to default to XP though if GRUB is easy enough to configure I'm happy to use that but need to know how to configure it to default to XP.

I've googled the GRUB man page, but there is a lot in there and most other posts refer to GRUB2.

Thanks

---

### Post by Bucky Ball on 2012-03-22
Easiest is to install Grub Customizer in Ubuntu:

[https://launchpad.net/~danielrichter2007/+archive/grub-customizer]("https://launchpad.net/%7Edanielrichter2007/+archive/grub-customizer")

Just follow the instructions. To get to software sources open update manager and hit 'Settings' bottom left.

Once installed you can set the grub timeout or change the order so Win boots first.

You would be well advised to be working with a stable, long-term support release if you are installing to a friend's machine (as you won't be there to nut out issues always). The current LTS is 10.04 which is supported for another 13 months. By mid-year 12.04 LTS will be fairly stable and it is a one click upgrade to it.

---

### Post by darkod on 2012-03-22
It's much easier to configure XP to be the default OS in grub2, as said above, than to use windows bootloader to boot linux. By default it can't boot linux and you have much more work to make that work.

---

### Post by Bucky Ball on 2012-03-22
Other thing to do is edit /etc/default/grub in a terminal.

Save the file so you have a backup:

```
sudo cp /etc/default/grub /etc/default/grub.backup
```Then open the file to edit:

```
sudo nano /etc/default/grub
```Look for the line at the top that looks like this:

```
GRUB_TIMEOUT="5"
```Yours probably has:

```
GRUB_TIMEOUT="0"
```... or:

```
# GRUB_TIMEOUT="5"
```... or something similar. Whatever it is, change it to:

```
GRUB_TIMEOUT="5"
```Once you've made the changes, hit x then 'Enter' and update grub:

```
sudo update-grub
```This change will give you a grub menu to choose the Win install from at boot.

Now, restart the machine and take note of where Windows is on the list (3rd position, 4th, wherever). Once at a desktop open the terminal and get to the file again:

```
sudo nano /etc/default/grub
```Look for the line that looks like this:

```
GRUB_DEFAULT=0
```Change the '0' to the number of the position of Windows. For example, if it was in the 3rd position, you would change it to:

```
GRUB_DEFAULT=3
```See if that works (when you boot let the machine sit for the timeout interval and default by itself; don't hit anything). If it does, you can go back and change the timeout line back to '0'. Once you do that change, don't forget to:

```
sudo update-grub
```... afterwards, and you're done. 

Like I said, installing Grub Customizer is the easy way as it can do all this for you via a friendly GUI. ;)

---

### Post by Oswiu on 2012-03-23
Thanks guys

Situation resolved. Due to an oversight on my part I had to rebuild the laptop again and I realised why I was getting the grub loader and not windows loader.
Previously I had installed windows and then whilst in windows installed Ubuntu, the option you get is to install Ubuntu INSIDE windows which then starts with the XP bootloader. This time however after installing XP I rebooted the PC with an Ubuntu install disc and was given the option to install ALONGSIDE XP and this meant the GRUB loader was used.
I also took your advice and installed 10.04 LTS, which uses GRUB 1.98 but the term line commands you gave still worked perfectly. It was all quite simple in the end.

There is one other query this threw up; I updated Ubuntu and found 2 extra boot option lines into the GRUB loader, I then set XP as the primary boot, so all was well. But what happens if more boot options are added with future updates. GRUB adds the new lines as 0 and 1, I presume the XP line that is currently option 4 will be changed to 6. but would GRUB.CFG be changed automatically to maintain the desired boot option or would I need to manually reconfigure it?

Apologies if my terminology isn't great, I still on the learning curve.

---

### Post by darkod on 2012-03-23
The order in which they enter in the menu depends on the order of the files in /etc/init.d/grub if I remember correctly. The two most important files are 10_linux (for ubuntu) and 30_os-prober for detecting the other OSs. Because the ubuntu starts with 10 and the os-prober with 30 the detected OS are at bottom and they move with new kernels installed.
No, grub config files will not adjust automatically.

What I usually do, is make another os-prober file with lower number than 10, and disable the 30. For example:
```
sudo cp /etc/init.d/grub/30_os-prober /etc/init.d/grub/06_os-prober
sudo chmod -x /etc/init.d/grub/30_os-prober
```

In this case return the value 0 in 
GRUB_DEFAULT=0

because windows will always be on top. Then run
sudo update-grub

to recreate the grub.cfg. After restarting you should see windows on top in the list and being the default OS to boot.

---

### Post by Bucky Ball on 2012-03-23
> **Oswiu said:**
> Thanks guys

Situation resolved.

Apologies if my terminology isn't great, I still on the learning curve.

No problems, excellent all working, you're doing fine and enjoy the learning curve! 

Please mark thread as 'Solved' from Thread Tools at the top right of this page to help others. ;)

---

### Post by Oswiu on 2012-03-23
Thanks once again, I think I have the basics of this now, I reset GRUB_DEFAULT=0 and copied the OS-LOADER from line 30 to 06 as you recommended and its using windows as the default boot OS and should after any further updates.

I assume the CHMOD line is to stop it searching a second time.

Took a bit of time to find, it was in /etc/grub.d/  not /etc/init.d/grub but that only made me read the correct literature, which I should be doing anyway.

Many Thanks

---

### Post by darkod on 2012-03-23
Sorry, my mistake. I'm not at home and don't have all the resources and an ubuntu machine. :)

The chmod with argument -x is to make the file not-executable. That way you avoid two os-prober functions searching for OSs. You can do the same for the 20_memtest if you want to get rid of that entry in the menu too. 

The files continue to exist and later you can always make them executable again by using chmod and +x.

---

