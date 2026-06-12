---
title: "Messed up windows boot during partition attempt"
date: 2010-02-19
forum: Installation &amp; Upgrades
---

### Post by macosxp on 2010-02-19
I tried installing as a dual-boot on a Dell Inspiron 9400,  but at the partition screen, after I set it to install along side  Windows, the progress bar just wouldn't move. Then when trying to boot  into Windows, it gave an error about wanting to reinstall  \system32\hal.dll and it won't boot. So I tried installing Linux again,  and it worked this time, but XP is still asking for hal.dll.

I  was thinking about going into recovery console with an xp install disk  and restoring hal.dll or repairing boot.ini or maybe fixmbr or some kind  of chkdsk, but I'm not sure what to do and I don't want to end up with 0  working operating systems.

How can I get Windows working right  again, preferably without messing up my only currently working OS, Linux?

---

### Post by stlsaint on 2010-02-19
> **macosxp said:**
> I tried installing as a dual-boot on a Dell Inspiron 9400,  but at the partition screen, after I set it to install along side  Windows, the progress bar just wouldn't move. Then when trying to boot  into Windows, it gave an error about wanting to reinstall  \system32\hal.dll and it won't boot. So I tried installing Linux again,  and it worked this time, but XP is still asking for hal.dll.

I  was thinking about going into recovery console with an xp install disk  and restoring hal.dll or repairing boot.ini or maybe fixmbr or some kind  of chkdsk, but I'm not sure what to do and I don't want to end up with 0  working operating systems.

How can I get Windows working right  again, preferably without messing up my only currently working OS, Linux?

You may just want to run a system repair on your xp partition with a xp disc.

---

### Post by macosxp on 2010-02-19
> **stlsaint said:**
> You may just want to run a system repair on your xp partition with a xp disc.
What is that, how do I do it, and how would it effect XP and Linux?

---

### Post by stlsaint on 2010-02-19
see here: [http://www.microsoft.com/windowsxp/using/helpandsupport/learnmore/tips/doug92.mspx](http://www.microsoft.com/windowsxp/using/helpandsupport/learnmore/tips/doug92.mspx)

and this will not affect your linux install as windows cannot "see" linux.

---

### Post by macosxp on 2010-02-19
> **stlsaint said:**
> see here: [http://www.microsoft.com/windowsxp/using/helpandsupport/learnmore/tips/doug92.mspx](http://www.microsoft.com/windowsxp/using/helpandsupport/learnmore/tips/doug92.mspx)

and this will not affect your linux install as windows cannot "see" linux.

Thanks.

Does that rewrite the grub bootloader, or rather, make a new nt bootloader? Will that erase any of my windows software or files? I'm also wondering if there's something simpler that I can do, in the recovery console, like doing fixmbr, fixboot or some way to repair boot.ini that will not be too difficult and will not mess up linux, windows, or the grub menu.

I would love some step-by-step directions for doing this on a dual boot and then replacing my old grub2 boot menu. Something written for a novice would be perfect.

---

### Post by pacmanic91 on 2010-02-23
I have done the EXACT same thing, about 4 days ago too! (your last post) 

Are you me!?

Try looking at your BIOS and the order in which the computer boots things, (suggestion from another website), however this didn't work for me.

If you have managed to solve it or got any further please please help :D

Thanks, 

Tom

---

### Post by pacmanic91 on 2010-02-23
And now the suggestion to put in the windows cd and follow the steps on the microsoft website, has further screwed things up :( (not blaming)

I didn't even follow all the steps, i only got to pressing f8 to agree to the license agreement. I couldn't understand what to do after that, i pressed R for repair and nothing happened. So i exited the setup and restarted my computer.

GRUB now doesn't load, Ubuntu therefore doesn't load, and neither does XP due to the missing hal.dll file!

Please help

Tom

---

### Post by macosxp on 2010-02-23
> **pacmanic91 said:**
> And now the suggestion to put in the windows cd and follow the steps on the microsoft website, has further screwed things up :( (not blaming)

I didn't even follow all the steps, i only got to pressing f8 to agree to the license agreement. I couldn't understand what to do after that, i pressed R for repair and nothing happened. So i exited the setup and restarted my computer.

GRUB now doesn't load, Ubuntu therefore doesn't load, and neither does XP due to the missing hal.dll file!

Please help

Tom
Actually, yes I did get XP working again, though I'm not sure what fixed it. Let me tell you what I did:

Boot into Windows XP CD
At the Welcome to Setup screen, push R to enter Recovery Console (pushing ENTER brings you to the install thing which then asks for the F8 license stuff, needed for a repair install, which is more of a last resort)
It will ask which XP installation to log on to and then it will ask your password. Choose the installation (eg, "1") and then type your password. If you don't have a password, leave it blank.
Ok, now everything else I did from recovery console:
First I tried fixmbr to repair the master boot record, and I also ran fixboot, and that didn't help.
Then I went back to Recovery Console and ran bootcfg /rebuild (fixes boot.ini which often causes hal.dll errors) and CHKDSK /r (which checks the drive for errors and fixes any).

And then XP works fine now.

Now the trick is to get GRUB2 back.
Since linux is in dev/sda5 I think this is the code I'm gonna need to try to run from a Live CD terminal:
```
sudo mount /dev/sda5 /mnt
sudo grub-install --recheck  --root-directory=/mnt /dev/sda
```Good luck!

---

