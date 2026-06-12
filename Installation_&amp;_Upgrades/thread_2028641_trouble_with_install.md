---
title: "trouble with install"
date: 2012-07-18
forum: Installation &amp; Upgrades
---

### Post by brennanm on 2012-07-18
Hi name's Matt. I got myself in a bit of a pickle. I downloaded Ubuntu  put it on a disc and attempted to install, did something wrong, and now I cannot restart windows 7 (restore disc failed) and the ubuntu program will only go as far as taking my log in and pass word, and then giving me another dos prompt and that's where I am stumped. I would like to just order the disc, but don't have a credit card. If there is some one out there that would send me a disc I would  kiss their feet and would happy to pay in advance for their troubles. Please would some most angelic person rescue me from the depths of despair.
  In my defense for this mess, I was watching over my two year old grandson while I was attempting this and if u ever saw the little bugger in action u would either  undertand, or think I'm a bigger idiot than ever for trying it in the first place with him afoot.

---

### Post by brennanm on 2012-07-18
Hi name's Matt. I got myself in a bit of a pickle. I downloaded Ubuntu put it on a disc and attempted to install, did something wrong, and now I cannot restart windows 7 (restore disc failed) and the ubuntu program will only go as far as taking my log in and pass word, and then giving me another dos prompt and that's where I am stumped. I would like to just order the disc, but don't have a credit card. If there is some one out there that would send me a disc I would kiss their feet and would happy to pay in advance for their troubles. Please would some most angelic person rescue me from the depths of despair. In my defense for this mess, I was watching over my two year old grandson while I was attempting this and if u ever saw the little bugger in action u would either undertand, or think I'm a bigger idiot than ever for trying it in the first place with him afoot.

---

### Post by lisati on 2012-07-18
*Thread moved to **Absolute Beginner Talk**.*

---

### Post by oldfred on 2012-07-18
From the liveCD you used to install, download and post the link from running BootInfo:

Boot Repair -Also handles LVM, GPT and separate /boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration.

If you can get to a command line, it may be video issue related. What video card do you have. 

Do you get grub menu?

If so try nomodeset.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
I had to do this with my Nvidia 9600GT:
To install Ubuntu, boot from the cd press any key at accessibility circle and keyboard, press F6 and then select the nomodeset option.
USB boot - At the menu press tab on the first option to edit the boot options and replaced the 'splash' option with 'nomodeset'. 
then
On first boot after install, press e on getting the GRUB bootloader menu. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode), install nVidia driver suggested my Ubuntu

---

### Post by Cheesehead on 2012-07-18
Did the install work the first time?

Does the GRUB bootloader countdown and then make the screen flicker?

Is the login screen graphical with pretty dots, or is it a text console asking for your login/password?

Are there any error messages? If so, please tell us *exactly* what they say.

Do you really think you did something wrong? If so, what? Or are you being polite about an installer failure?

---

### Post by epikvision on 2012-07-18
Did you choose the right XX-bit image to install into the computer?  The only solution from here is to have a fresh copy of Ubuntu and reinstall it.  Now that your Windows is gone, you can always reinstall it as well if you have the disk.

Remember, Ubuntu is always free.  You can ask someone to download the image, burn it to a cd, and give it to you.

---

### Post by mebomechanicno1 on 2012-07-18
Starting from basics, which "distro"  (version of linux/ubuntu) did you try to install, and when you say you "put it on a cd", did you burn it or drag it?  You may be better to try to start again by burning Ubuntu 12.04 onto a disc and reboot from that.

---

### Post by brennanm on 2012-07-18
Thanks oldfred. Been trying to follow your lead but after chasing this around abit I notice all the examples on the down load page show entirely different than what I'm getting. I'm looking at la dos display. I really can't help to think that I got a glitch either from the down load or burning the disc. Thanks again tho.

---

### Post by oldfred on 2012-07-18
Do you get grub menu? or do you have to hold shift from BIOS until menu appears.

Or:
What appears on command line, if grub> or grub rescue> it has not booted. You will not get grub menu. Run BootInfo from Boot-Repair.

But if you get a login and can log in, it almost for sure is a video issue. Try adding nomodeset to linux line in grub menu as the screenshots in link above show.

---

### Post by brennanm on 2012-07-18
Thanks mebomechanicno1, boy that's a great name. Yes I did burn it. Had the instructions on my mobile while I was doing that part. I'm sure if one just drug it across it would look like their example of an incorrect display. Still plugging away

---

### Post by lisati on 2012-07-18
Threads merged so that the community's efforts aren't diluted.

---

### Post by oldfred on 2012-07-18
Some systems seem to get confused after too many boot errors and will not boot from a CD.

Sometimes a full power down or cold boot then works to reset everything. Some systems require both the BIOS and the one time boot key (f12 on my system but it varys) to choose CD or USB.

---

### Post by brennanm on 2012-07-19
Thanks every body. Sorry that I have not been thorough enough for u guys so far, been trying to keep it short cuz its tuff to type much on this mobil with these fingers.
First hello cheesehead. No on the install and flicker, blackscreen with only "log in" then password. After I enter the pass word, some more dos stuff that would take me a month to type and a prompt at the end. And the most important question, yes I do believe I did something wrong. People who know me say I'm a pretty smart guy but I know well my tendency to do some pretty dumb shhtuff. To start with when I tried to use my recovery disc it could not operate because it said it was missing a image file (it didn't specify which) the first indicator of messing up. So after another attempt at installing ubuntu to the same end, and another attempt at recovery, I elected to wipe my disc. And try again at the install. This is when I discovered is u guys. At this point if it hadn't been for Oldfrank I would have already have thrown in the towel. 
 So Frank got me to the point of finding the grub screen and f6. This is when I realized that it was not a trial install, it was the full thing. This migiht explain the "missing image file"  from windows restore disc. Hence the dumby me theory. I picked  nomodeset and ran it again with the same result. Started once more to the point I'm at now. I'm on the install screen, I've again chosen nomodeset. Above the f menu bar it shows:

Boot Options 'preseed/ubuntu-server.seed vga*788 initrd*/install/initrd.Hz quiet--

From the web pages oldfrank sent me to it seems to me that that nomodeset ought to be showing up there. Does that help? Don't give up on fellas.

---

### Post by brennanm on 2012-07-19
Oops forgot to add that on that boot options line I had to substitute * for an equal sign cause my phone lacks one.

---

### Post by oldfred on 2012-07-19
What version are you booting?

The options should let you add nomodeset.

---

