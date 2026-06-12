---
title: "[SOLVED] Ubuntu Partition Manager"
date: 2006-11-12
forum: Installation &amp; Upgrades
---

### Post by shankariyer on 2006-11-12
Hi,

I've a HP Pavilion dv6000z laptop and I opted to manually edit/set partitions.
But it keeps complaning 'set the root file system'... This is what I've...

> partition|file system|size|flags|
/dev/sda1|ntfs|52gb|boot|
/dev/sda2|fat32|11gb|lba|
/dev/sda3|ntfs|1gb||
/dev/sda4|extended|9.7gb|lba|
/dev/sda5|ext3|9.48||<---------------------Created using Norton Paritition Magic
/dev/sda6|swap|290m||<---------------------Created using Norton Paritition Magic


I just choose forward to go to the next screen...

> Mount point|Partition
/media/sda5|Partition...sda5
/media/sda1|Partition...sda1
/media/sda3|Partition...sda3
/media/sda2|Partition...sda2
swap|Partition...sda6
last row is empty for both Mount Point and Partition

In the above screen, I tried to change the /media/sda5 to "/" as it suggests, but
it still complains 'no root file system'.

Please advice.

Thanks,
Kramer.

---

### Post by catlett on 2006-11-12
Make sure you are selecting 'reformat'. It will be a check box after the drop down box where you select /. If you don't let it reformat the space it will not be able to reformat and indstall the root file system, which will give you that error.
Try that and see if it solves the problem. If not, post.

---

### Post by suguru on 2006-11-12
I also clicked reformat but I still got the same problem on my laptop.

---

### Post by catlett on 2006-11-12
That's strange. You have everything you need. You have a swap and a root. sda5 is already created and ready for the root file system and your swap is there. The partition has more than enough room with 9 and a half gigabytes. It doesn't make sense. I'll search for a bit but this is an example of an error that drives me crazy. Everyuthing is "right" yet it is coming out "wrong". Obviously there has top be a reason for the error, not it is just an issue of finding it.
I know you already know how to do the install, but here is one I like to refer to [http://www.debianadmin.com/ubuntu-edgy-eft-desktop-installation-with-screenshots.html](http://www.debianadmin.com/ubuntu-edgy-eft-desktop-installation-with-screenshots.html) Go over it and see if anything 'pops out' at you that seems different than what you did.

---

### Post by shankariyer on 2006-11-13
So near, yet so far...

I selected the partition ( I had previously created using Partition Magic ) deleted it and the swap also and created both.

In doing so, I found that if I choose back ( after that point ), it'd go crazy and not show those newly created partitions ( ext3 and swap ).

Anyway, the installation went fine, but now after reboot and choosing the new installation from grub, doesn't get me to the login screen.

It shows the Ubuntu logo, progress bar is shown and the screen goes blank and keyboard is deactivated I guess ( caps-lock, scroll-lock don't respond ).

One note, when I started the installation, the very 1st screen, where I had F4 option to change the resolution, I had to use it before, as by luck, I found that if its set to VGA, it'd be blank, so I changed it 1024x768x32 and only then I was able to go thro' the installation options.

Back the issues, just before this black out, I was doing alt-f1, I was able to glance that after it shows the entries and comes to the prompt 'machine-name:', it dies.

Pl advice, Thanks.

Kramer.

---

### Post by shankariyer on 2006-11-13
My video card is Nvidia, GeForce Go 7200.

---

### Post by shankariyer on 2006-11-14
I opted 'recovery' menu option. I was able to get to the prompt.
'boot' is under '/', it has everything I could remember seeing in my
last Linux distro( Ubuntu ).

For every few seconds, I saw this one pop-up
"usb 1-4: device not accepting address-6 error 110"

And then in about 2-3 mins, the system froze and now I'm unable
to get to the prompt using the 'recovery option' also.

What do I do ?

Tx.

---

### Post by catlett on 2006-11-14
What is plugged in your usb ports? Is it somethimng that can be removed? 

I mjust did some searching (just a tip, when I troubleshoot linux problems, I just copy/paste the error code, numbers and all, into google. It always gives a return of forum threads and mailing lists threads with the same issue) This appears to be a kernel issue. It also appears you may have run into your first 'bug'. Bugs are problems with the kernel or OS that reappear continually and are not a result of user error.
I found one thread with an answer but it is beyond my abilities. It involves patching the re-compiling the kernel. It is found here in case your interested [http://groups.google.com/group/linux.kernel/browse_thread/thread/30a048dc8a894554/19de3ac9902aeba6?lnk=st&q=usb+1-4%3A+device+not+accepting+address-6+error+110&rnum=4&hl=en#19de3ac9902aeba6](http://groups.google.com/group/linux.kernel/browse_thread/thread/30a048dc8a894554/19de3ac9902aeba6?lnk=st&q=usb+1-4%3A+device+not+accepting+address-6+error+110&rnum=4&hl=en#19de3ac9902aeba6)
This is the google return I got just in case you are interested. [http://groups.google.com/groups?q=usb+1-4:+device+not+accepting+address-6+error+110&hl=en&lr=&safe=off&sa=X&oi=groups&ct=title](http://groups.google.com/groups?q=usb+1-4:+device+not+accepting+address-6+error+110&hl=en&lr=&safe=off&sa=X&oi=groups&ct=title)

Just to let you know what I would do. If you are using the 64 bit Ubuntu, I would try the 32 bit. If that is not the issue, I would try installing Ubuntu version 6.06 Dapper Drake. Dapper is the release before Edgy but it is also the long term support release. So Dapper is still current and viewed as more stable. Switching to a dapper install may do the trick.
Sorry for the lack of help. Compiling kernels and kernel patches are beyond my abilitites. Good luck and hopefully someone with more ability comes upon the thread.

---

### Post by shankariyer on 2006-11-16
[FONT=Verdana]Suspecting, I installed without any USB devices plugged in, but no luck.

I was able to briefly spend some time in the command prompt, checked /var/log/dmesg
and I saw this ( don't know if its the reason or means something... )

"error : microcode bcm43xx_microcode 5-fw not available or load failed"

After a short while, it all froze and I had to reboot hard way. This was the recovery option.

The normal option doesn't even come to the login screen.

Pl. advice.

Thanks.
[/FONT]

---

