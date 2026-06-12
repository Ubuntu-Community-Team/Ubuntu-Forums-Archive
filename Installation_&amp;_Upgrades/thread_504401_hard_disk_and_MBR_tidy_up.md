---
title: "hard disk and MBR tidy up"
date: 2007-07-19
forum: Installation &amp; Upgrades
---

### Post by snakra on 2007-07-19
Hello,

I installed 6.10 on my laptop alongside Windows XP Pro Tablet.

I had a bit of a problem so I tried a fresh install and it worked fine for a time until it failed to boot and requested a manual fcus, which I did and it now works again - but it left a few more lines on the MBR

This has all left start-up menu in a mess of different versions. Can any body help and show me in simple terms how to tidy up the MBR without upsetting the two working OSs.   

How can I reorder the MBR so that the first item to be the Windows so that the default boot is with Windows and [I] have to manually select boot with Ubuntu.

Many thanks

SN

---

### Post by davidjmayo on 2007-07-19
To change XP to boot first see this link
[http://ubuntuforums.org/showthread.php?t=497342](http://ubuntuforums.org/showthread.php?t=497342)

while you are in the /boot/grub/menu/lst anything you don't want to appear you can comment out with # at the start of the line (you will see some lines done like this already)
to make it boot quicker into XP see the line with timeout (should be 10 as in 10 secs. change to 2)
HTH

---

### Post by snakra on 2007-07-20
Dear Davidjmayo,

Many thanks for your prompt reply.

Your advice and redirection to the relevant threads successfully allowed me to do what I wanted.

For somebody like me who is a novice with Linux and Ubuntu this support is thankfully received

Yours

SN

---

