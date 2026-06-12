---
title: "Karmic 9.10-Grub2-Boot Menu Problems"
date: 2010-02-09
forum: Installation &amp; Upgrades
---

### Post by jamere on 2010-02-09
Hi folks.

I have an Acer Aspire One Netbook that is dual booting Win XP and Karmic 9.10. I did a clean upgrade to 9.10 from ISO image with no problems. 9.10 is up-to-date via Update Manager. I now have Grub2 1.97 beta 4 via the Karmic install.

Problems:
1) old boot menu items are [COLOR="Blue"]NOT[/COLOR] removed even when removed completely from Synaptic package manager.

2) newer kernel versions arriving via Update Manager aren't displaying in boot menu.

Old 9.04 versions are displayed in the menu as well as Xubuntu versions. Xp and Vista are menu choices also.

Any advice or ideas would be much appreciated. Have never had to deal with a single Grub issue in 3 years of using Ubuntu. Hope this isn't a show stopper for me as I've enjoyed using ubuntu to this point, anyway! ;)

Thanks much!

---

### Post by wkulecz on 2010-02-09
Haven't you heard, Grub2 is better.

I don't see it, this Emperor has no clothes as far as I can tell.  I'm having lots of issues maintining grub2 and a multi-boot system.  If you get an answer it'll probably help me too.

---

### Post by jamere on 2010-02-09
wkulecz,

Yeah, I didn't even know what "grub" was until I installed Karmic 9.10! :D:D  Doesn't bode well for new, non-techie users.

I also have another show stopper issue I won't even go into here other than to say it deals with Qualcomm usb modem (broadband wireless) on my Netbook. Have to boot in XP then restart in 9.10 in order to load modem firmware to connect network. So far, I can't boot independently of Win XP...sheesh. :confused:

---

### Post by darkod on 2010-02-09
> **jamere said:**
> Hi folks.

I have an Acer Aspire One Netbook that is dual booting Win XP and Karmic 9.10. I did a clean upgrade to 9.10 from ISO image with no problems. 9.10 is up-to-date via Update Manager. I now have Grub2 1.97 beta 4 via the Karmic install.

Problems:
1) old boot menu items are [COLOR=Blue]NOT[/COLOR] removed even when removed completely from Synaptic package manager.

2) newer kernel versions arriving via Update Manager aren't displaying in boot menu.

Old 9.04 versions are displayed in the menu as well as Xubuntu versions. Xp and Vista are menu choices also.

Any advice or ideas would be much appreciated. Have never had to deal with a single Grub issue in 3 years of using Ubuntu. Hope this isn't a show stopper for me as I've enjoyed using ubuntu to this point, anyway! ;)

Thanks much!

What is a "clean upgrade"??? People usually say clean install OR upgrade, not clean upgrade.
If you did upgrade from 9.04 to 9.10, then grub remained as grub1 unless specifically upgraded too. But you claim to have grub2.
If you are sure about that, did you try running:
sudo update-grub

after removing kernels in Synaptic? For the new grub2 you have to run update-grub after any change so a new updated grub.cfg file will be created.

If by any chance you still use older grub1, as far as I know it doesn't automatically update the menu list, so you have to do it manually. That is one good feature of the new grub2 here that you criticize. But I don't even want to get into that especially with wkulecz because all you can see from that user here is criticism.

Further more, if you really want to learn about your boot process or at least provide correct information for someone to help, I suggest you download and run the script from my signature, move it on desktop for example, and run it with:

sudo bash ~/Desktop/boot_info_script*.sh

It will create results.txt file with detailed info. Copy the content of the file here and wrap it in CODE tags for easier reading (with the text selected hit the # button in the toolbar above). From those details we might figure out something.

---

### Post by jamere on 2010-02-09
Darko...you must be in "public relations work"! Thanks anyway for the reply which was informative.

> I did a clean upgrade to 9.10 from ISO image with no problems 

How much clearer can I make it for you? What is it you don't understand?

> But you claim to have grub2.
If you are sure about that, did you try running:
sudo update-grub

I not only claim to have Grub2...I do have it. At least it says 1.97 beta4 on the boot menu screen. It either came in the 9.10 install or via Update Mgr. I had no way of knowing to run: sudo update-grub

As I stated previously, I'd never had a problem with Grub and didn't have occasion to know what it was, as it was never an issue until Karmic.

> That is one good feature of the new grub2 here that you criticize. 

If you read my statement closely, you will see that I complimented Ubuntu and have used it with no problems to this point (3 years).

I really don't want to waste my time and energy replying to your snide reply. You really have good info to impart to others, but I suggest an attitude adjustment on your part or you'll run off folks with legitimate problems.

Please re-read my original statement...there was NO criticism...only a compliment!

Have a great day!:D

---

### Post by oldfred on 2010-02-09
You spent a lot of time replying when you should be posting the results.txt that tells us how your system is configured. We find many users who do not know exactly what they have and this script greatly helps in resolving boot issues.

Script also worked for the many issues we had with old grub (0.97) and new grub has some issues still but mostly with raid, multidrive setups where the user is not sure what drive boots first and some software by HP and Dell in windows that uses the MBR for other than booting which corrupts the boot process.

---

### Post by oshunluvr on 2010-02-09
> **jamere said:**
> Hi folks.
I did a clean upgrade to 9.10 from ISO image with no problems.

Old 9.04 versions are displayed in the menu as well as Xubuntu versions. Xp and Vista are menu choices also.

I can't speak for darkod, but MY confusion here is did you UPGRADE (via upgrade manager) or did you do a new INSTALL from the iso? The difference being 9.04 and previous used GRUB-Legacy and 9.10 uses GRUB2. If you UPGRADED you don't automatically get GRUB2. The install methods are different and could make the problems different.

Seeing that you have 9.04 choices still in your menu leads one to believe you did not so a clean install. If you did a install from the iso installer over your old install without reformatting and wiping the old install off - you would be having these problems...

---

### Post by jamere on 2010-02-09
Hey guys,

Sorry for the confusion. I'm pretty sure the boot menu problems are due to the several ISO versions (9.04, Xubuntu, 9,10) I downloaded and installed on my Acer Aspire Netbook alongside Win XP, trying to find a version that would connect to broadband wireless network (alluded to in Reply #3 above). This is a real problem affecting many users and as far as I know, still unsolved. If interested, see my thread here:
[http://ubuntuforums.org/showthread.php?t=1330488]("http://ubuntuforums.org/showthread.php?t=1330488")

Anyway, thanks for the help here. Think I'll wait for 10.4 and maybe both problems will sort themselves out. Cheers!

---

