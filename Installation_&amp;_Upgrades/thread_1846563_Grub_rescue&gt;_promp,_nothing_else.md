---
title: "Grub rescue&gt; promp, nothing else"
date: 2011-09-19
forum: Installation &amp; Upgrades
---

### Post by petri on 2011-09-19
After installation of W7 and Ubuntu 10.10 I didn't reach Grub only the prompt "Grub rescue> ". Now I have reformatted this harddrive, reinstalled Ubuntu and still can only see this prompt of Grub rescue. It didn't help install W7 either it didn't clean up MBR. 

At the moment I can't use my computer because I can't boot any of the installed OS. Is there any way to uninstall Grub for good?

---

### Post by YesWeCan on 2011-09-19
Can you boot live CD and run
sudo sfdisk -luS

---

### Post by varunendra on 2011-09-19
Installing win7 over ubuntu MUST be able to replace grub. I doubt it is a case of multiple drive confusion. Awaiting output of *YesWeCan's* commands.

---

### Post by petri on 2011-09-20
Thanks

and sorry but there is no output to give. I was in hurry so I disconnected all drives except the one with the OS. And "Grub rescue" was still present at boot but after I installed W7 it worked as it should. This time windows did write new MBR in the right drive.

Then I connected the rest of the drives and installed 10.10 but grub didn't show upp. Searching in this forum gave me  [Boot-repair]("https://help.ubuntu.com/community/Boot-Repair") (in some thread where YesWeCan linked to it) and that did fix my Grub.

Everything works now. Well not 5.1 the sound with HDMI but that is another thread.

---

### Post by varunendra on 2011-09-20
Great!
I guess this must be what happened earlier:

For some reasons unknown to me (but it happens sometimes) grub was installed on a drive which was top in BIOS boot priority, but did not point to the correct drive/partition where its configuration files were located (ubuntu partition). Hence the grub prompt.

OTOH, Windows detected some other drive as the first drive (most probably, but not necessarily, on which it was installed itself), and installed its boot loader on that drive's MBR. But that was not the top drive in boot order. In that case, merely changing the boot order should have worked.

But it is just a hypothesis, things with multiple drives/partitions may sometimes get much more complex. The best part is: they 'can be' fixed no matter how complex they are, once understood correctly. And the best part for 'you' is - you got it resolved anyhow ;)

So how about putting a link to the thread that helped you (if you remember) and marking this one as [solved].:popcorn:

---

### Post by petri on 2011-09-20
I linked to Boot-repair which I found in som thread which was not for my problem so I don't remember what it was.

I have an PCI controller card for SATA and drive connected to that appears as the first one with "sudo fdisk -l" and that on might have been the problem. I installed that card after I had installed previous OS:s. In Ubuntu it worked fine and W7 I never booted.

---

