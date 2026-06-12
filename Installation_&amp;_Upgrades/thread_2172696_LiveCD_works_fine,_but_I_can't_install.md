---
title: "LiveCD works fine, but I can't install"
date: 2013-09-06
forum: Installation &amp; Upgrades
---

### Post by amanchesterman on 2013-09-06
I have an Acer laptop on which I have run Windows XP and various versions of *buntu (dual boot) for the last year. For a while I had xubuntu installed, but a few months ago I replaced it with Bodhi Linux. I'd now like to revert to xubuntu 12.04 LTS -- a fresh install, replacing Bodhi completely. I have made a liveCD, the checksum is correct, and xubuntu runs perfectly from it. But when I try to install it, there is a short pause and the machine crashes completely: I get a black screen covered with white text and I can only restart by switching off.  The crash happens **before** I get any options about installing to different partitions: it's right after clicking 'install'.

I've installed from liveCD before and have never encountered a problem like this so I am baffled. The machine is clearly capable of running *buntu (Bodhi is working fine) and the liveCD has no flaws -- so what's wrong?

---

### Post by varunendra on 2013-09-06
32 bit or 64 bit?
Have you tried various boot options? Especially 'nomodeset' : [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

I'm not aware of how Xubuntu installer works, so please correct me if I'm making any wrong assumptions - does it make any difference if you choose to "Try" (live session) then start the installation from there?

---

### Post by Quackers on 2013-09-06
Sounds like a kernel panic maybe noapic, nolapic or acpi=off could also be boot options you could try.

---

### Post by Bucky Ball on 2013-09-06
*Thread moved to **Installation & Upgrades**.*

Please post in appropriate sub-forum. Cheers. ;)

---

### Post by amanchesterman on 2013-09-06
Hi and thanks for your suggestions -- and thanks to Bucky Ball for moving this to the right forum.

To clarify a couple of points first:
- I'm using the 32 bit version, which is the one I used before and is the version currently used by Bodhi.
- The xubuntu installer is visually and functionally the same as the main ubuntu installer. So far as I'm aware, xubuntu and ubuntu are the same 'under the hood', it's just the desktop interface that's different.

To respond to your suggestions:

@varunendra: I booted the LiveCD and opted to 'try' xubuntu. It works perfectly -- applications, network etc. It 'sees' the partitions on the hard disk, i.e. Windows and Bodhi Linux / and /home. It's from that desktop that I clicked the 'install' option, and that's when the installer crashes.
I'm sorry but I don't really understand your suggestion about 'nomodeset' and the other boot options. I'm a beginner when it comes to all this so it's probably due to my ignorance -- but my problem, as I perceive it, is not about **booting** Ubuntu at all: it boots (i.e. loads and runs) perfectly well from the LiveCD. My problem is about **installing** it, i.e. copying the stuff on the LiveCD on to the hard disk in order to replace Bodhi Linux that's there. How would 'boot options' affect installation? and where would I select them, if that is indeed what I need to do? The 'try xubuntu' desktop doesn't offer any options about installation: there's just a single icon labelled 'install'.

@Quackers: Same point, really. I don't really understand the options you suggest and I don't know how to implement them -- but do they affect installation anyway? Ubuntu boots perfectly from the LiveCD and the Linux kernel used by Bodhi (currently 3.8.0-12-generic) runs with no problem -- so I don't see that 'boot options' are what I need.

Apologies to you both if I seem obtuse! I'm a beginner, as I said, with limited experience of Linux, though I've used it for a while. I'm willing to try solutions if you can give me step-by-step instructions.

---

### Post by varunendra on 2013-09-06
Just follow the link I gave you. It not only explains the various available boot options, but also tells how, when and from where to use them.

The nomodeset option just boots the live os in basic graphics mode. So if there are any graphics related issues (which is most frequent case), they are circumvented.

The options that Quackers suggested, as much as I understand them, disable some advanced interrupt controls that may sometimes cause issues with some hardware.

You can get a summary table of available options and what they do in the "[Common Kernel options]("https://help.ubuntu.com/community/BootOptions#Common_Kernel_Options")" link at the bottom of the same page.

---

### Post by amanchesterman on 2013-09-06
Thanks Varun, I have read the link you recommended and I'm working through the options. No luck so far, the installation keeps crashing as before.

In case it's any help to you, on the page displaying the crash messages, the first line that I can make any sense of reads:

Pid: 5922, comm: modprobe Tainted: P W O 3.2.0-52-generic #78-Ubuntu Acer Aspire 3690 /Grapevine

Further down there's another reference to 'Process modprobe' and then something about a 'stack' with a load of numbers and then a whole series of lines beginning 'Call trace:'. I assume this is debugging information, is it any use?

---

### Post by varunendra on 2013-09-06
It suggests possibly a buggy driver may be the culprit, but doesn't give any hint about which driver.

Hopefully, the most common ones causing such issues will be taken care of by one of the options. You can use more than one at a time.

---

### Post by Bucky Ball on 2013-09-06
I noticed this is now marked as 'Solved'. Any chance you could share with the community how you fixed your issue, please? ;)

---

### Post by amanchesterman on 2013-09-06
Many thanks Varun, I have xubuntu installed now. I chose the 'noapic' option -- but your comment about a buggy driver reminded me that this Acer model has a wireless card that doesn't work well with the default Linux driver, so when I came to the installation page I **didn't **check the options for 'download updates while installing' and 'install third-party software'. Consequently (I think) the installation didn't try to connect to the internet and the installation proceeded smoothly.
Thanks again for your patience and helpfulness!

---

### Post by varunendra on 2013-09-06
> Thanks again for your patience and helpfulness!
My pleasure ! But it's you who got it sorted. :)

For others, it may not be just one of the drivers, may as well be one of the updates causing kernel panic during configuration.

The take-home lesson is - do not enable "Updates" and "Third party software" **during** installation when having such crash issues. You can do these later when the system is installed.

---

### Post by Quackers on 2013-09-06
I would endorse that view. I once had a perfectly good iso image that booted into live mode just fine but would give a kernel panic on attempting to install. 
Having realised that I had ticked the download updates box I tried again without it being checked and the installation went ahead normally.
Not sure what caused it exactly, but it worked.

Glad to hear you've got it installed anyway.

---

