---
title: "When will Ubuntu 8.04 be fixed ?"
date: 2008-07-12
forum: Installation &amp; Upgrades
---

### Post by skozzy on 2008-07-12
I downloaded another ISO of ubuntu 8.04 and still can't install it on my computer, I get stuck at a busy box thing like most do. I can't believe the available ISOs to download havn't been fixed. How many people out there are being turned away from linux and sticking with windows cause of this. If there is a work around why can't someone patch the ISO to make it into a easy working install.

Apart from that if I install 7.10 will it work ?

I know the software is free, but at least the installer should work.

---

### Post by upchucky on 2008-07-12
busy box is indicator of grub failure not bad disk.

does the iso you made boot from cd-rom drive? if so it is fine.


if you installed it and got busybox, then it is installed and grub loader needs information to boot it, if you are dual booting then grub needs infor on where you installed linux and windows.

there are thousands of posts here that help, but you gotta be more specific when asking for help.

search for grub, booting, partitions, menu.lst, dual booting as the need requires for your particular install.

search my name as well as pumalite for posts, there are extensive answers to many installs

---

### Post by SkonesMickLoud on 2008-07-12
Did you check the md5sums of the .iso?

Did you burn at 4x or less?

Did you verify the integrity of the CD?

Have you tried the Alternate CD?

The best way to get help on here is to be as specific as you can be.  No one minds helping you out, we just have to know more about what is wrong.

---

### Post by ajgreeny on 2008-07-12
> I downloaded another ISO of ubuntu 8.04 and still can't install it on my computer, I get stuck at a busy box thing like most do.No, most don't.
I have been using ubuntu in particular and other linux distros just to try them out for 3 years and I have never yet had a problem getting anything to install or run on my machine.  You appear to have either a hardware incompatibility issue or a problem with the burning/download of your iso to CD.  You can not really blame ubuntu for either of those two problems as they are not really a problem that ubuntu can do anything about.

Do what SconesMickLoud says and you may get somewhere.

---

### Post by skozzy on 2008-07-12
Ok I see I didn't word it all correctly.

I used to have a working 7.10 install, it later was updated to LTS8.04, after that time non of my SATA drives nor my PCI IDE drives showed up and the boot took over 5 mins. At that time there was no mention about a work around so I formatted the drive to install the new 8.04 version.

Now it's the same problem, the cd will boot to the main menu but the CD won't boot into the livecd nor will it install, it stops in a busybox shell thing.

I have read that you do this and you do that, but I can't even get to a dos/shell prompt to do anything. It seems that people are finding ways to make 8.04 install but have to do a bit of work to get it to happen, what i'm asking is why after a month or 2 since 8.04 was released that the problem with SATA drives (HD or CD-Rom) hasn't been fixed in the distro iso. Imagine if you bought windows xp or windows vista and it won't install cause your new computer has hardware not supported. I know ubuntu is free and is built on the love and free time of people around the world. But surely someone can fix the Hard Drive/CD Rom detect on the Distro ISOs so people like me who don't know how to fix things can just do a simple install without being stuck.

I'm not asking how to get around the install problem its been answered several times I see, I just won't use it on this computer anymore, my question relates to the downloadable ISO, why is it still available as a mostly non working install, surely it can be fix/patched so a new person to linux (like me) can install with no fuss.

I am thinking of redownloading v7.10 ubuntu and installing that, but before I go over my download limit I'd also like to know if v7.10 has the same problem now like 8.04 does or does it still work. I had it installed on this computer before and I think the upgrade from 7.10 to 8.04 is what killed it.

My main computer has 2 IDE ports and 4 SATA ports on the main board and a PCI card with 2 IDE ports, I have 6 IDE hard drives 4 SATA hard drives and 1 IDE DVD Burner and 1 IDE DVD Rom. One or more of these drives or the ports they are on must be apart of the problem or the install not detecting one or more of the drives correctly.

Anyhow, I am starting to rant and thats not helping anyone, I do appologise. I just want an easy to install Ubuntu like there was with v7.10 and I think others in my situation would like the same.

---

### Post by skozzy on 2008-07-12
I have downloaded ubuntu 7.10 iso, burned it and now at the time of typing this I have booted the livecd and all the hard drives are detected.

So if v8.04 lands me in a busy box and v7.10 boots fine does that still mean I have a hardware problem or that there is something wrong with the install/boot of the livecd for v8.04

I will now attempt installing v7.10 and post back with my results.

---

### Post by avtolle on 2008-07-12
It is my understanding that the issue with SATA drives is one related to the kernel being used in 8.04, and is not limited to Ubuntu and its variants but affects other distros using this kernel. I have read that this will be "fixed" in the newer kernel to be used in 8.10. 

Of small comfort to the OP, to be sure. Hope the kernel upgrades that have occurred in 7.10 recently do not adversely affect his usage.

---

### Post by skozzy on 2008-07-12
Well ubuntu 7.10 installed fine and I am using that right now. All hard drives have been detected and everything is super fast.

I guess I wait till 8.10 is released and try my luck again. 

If I don't choose LTS 8.04 update will the updates that become available keep this v7.10 install or will it change v8.04 ? If v7.10 works I will stick to that.

---

### Post by avtolle on 2008-07-12
So long as you don't select to update to 8.04 LTS, the updates (security only, as I understand, unless you have the backports repository enabled) will keep your 7.10 at 7.10. As you know, unless things change, you won't be able to do a direct upgrade to 8.10 through the update manager, but will need to do a clean install of 8.10 should you decide to upgrade to that in the future.

Good luck.

---

### Post by skozzy on 2008-07-12
Ok thanks, well lets hope when v8.10 is available EVERYONE can install it from the livecd and not just those who know the in's and out's of fixing broken things.

---

### Post by avtolle on 2008-07-12
Unless things really change, I'll need to use the alternate install CD for installation; this has been true since 7.04 on my "mature" hardware. :-)

---

