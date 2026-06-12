---
title: "can't boot after update"
date: 2010-10-11
forum: Installation &amp; Upgrades
---

### Post by dgel on 2010-10-11
Hi,

I updated from 10.04 to 10.10 this afternoon, and after a reboot, I can't start ubuntu in the new kernel. Grub shows up fine, but after selecting the new kernel, all disk activity stops after a while. When booting in safe mode, the same thing happens.

Oddly, booting in the old kernel does work. I'm not sure which log files might be of use here, so haven't gotten much further..

[edit]
Just tried to boot in the livecd, doesn't work either, same problem.... I guess there is a driver problem somewhere most likely

---

### Post by aksoutherland on 2010-10-11
I have the same issue on my Samsung NC10 Netbook after upgrading from 10.04 to 10.10. I didn't have time this morning to investigate properly, but will look into it this evening. If I find anything I will let you know.

I am unable to boot to the new kernel, but can boot to the old kernel. That was as far as I had made it this morning before I had to leave for work.

---

### Post by Peter09 on 2010-10-11
when you get to the grub menu press the 'e' key (for edit) add the 'noquiet' option to see the text while it boots. I believe hitting the escape key while booting may have the same effect. This should tell you where it is stalling.

---

### Post by satet on 2010-10-11
I had a similar situation after an upgrade to 10.10. To fix it until software updates fix the problem permanently (I hope) try this. When you get the boot screen, choose the 'e' option. This will display an editor screen of the boot steps about to be taken one of which has options like "splash" etc. To that line add acpi=off. This is a temporary change and will not be remembered on the next boot. Unfortunately, you will not then be able to put the computer to sleep, but you may be able to run the new kernel (2.6.35). If this works, you can make the change permanent, I think, by editing the /etc/default/grub file.

---

### Post by aksoutherland on 2010-10-11
I found that my issue was actually this.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/642421?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/642421?comments=all)

I booted to the previous kernel and ran sudo update-grub.
This allowed me to be able to boot to the new kernel so that I could get the full error message. A quick google search of the error turned up the above link. There is a work-around posted in on the page. It worked to get me up and running on the newest installed kernel.

Hope this helps.

---

### Post by dgel on 2010-10-12
I tried the acpi=off workaround and it worked for me. Let's hope there will be a kernel update soon.

For those wondering if they have this specific problem, when I add no-quiet, booting stops after the following three lines:

[1.728947] lo: disabled privacy extensions
[1.729182] NET: registered protocol family 17
[1.729858] registered taskstats version 1

---

