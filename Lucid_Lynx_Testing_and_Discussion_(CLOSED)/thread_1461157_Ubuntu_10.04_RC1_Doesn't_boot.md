---
title: "Ubuntu 10.04 RC1 Doesn't boot"
date: 2010-04-23
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by dom96 on 2010-04-23
Hello, whenever i try to boot with the Ubuntu 10.04, i get the loading screen(with the dots), after that all i get is a message saying 'The installer encountered an unrecoverable error. A desktop session will now be run so that you may investigate the problem or try installing again.'

Is anyone else experiencing this issue ? Does anyone know what it means ?

---

### Post by cariboo on 2010-04-23
Have you tried using nomodeset to start? At the initial screen, press the any key, chose your language, then press F6, select nomodeset, then continue on to the desktop.

---

### Post by dom96 on 2010-04-24
Thank you, that works. May i ask what does nomodeset do ?

---

### Post by dino99 on 2010-04-24
disable the kms stuff

---

### Post by phibxr on 2010-04-24
> **dom96 said:**
> Hello, whenever i try to boot with the Ubuntu 10.04, i get the loading screen(with the dots), after that all i get is a message saying 'The installer encountered an unrecoverable error. A desktop session will now be run so that you may investigate the problem or try installing again.'

Is anyone else experiencing this issue ? Does anyone know what it means ?

I get the same error message on four separate machines with very different configurations.

A bit disturbing this close to the final release.

---

### Post by chris1379 on 2010-04-24
Same problem here. I was able to install it by hitting a key at boot, choosing language, and then choosing to try without installing. Once it got to the live cd desktop, I clicked on the install icon and it went just fine.

BTW, I did a search and can't find anything telling me what the different options like "nomodeset" do. Where can I find that.

---

### Post by dom96 on 2010-04-24
I cannot find anything about the "nomodeset" option either.

---

### Post by amano on 2010-04-24
It seems that some more cards should be added to the KMS blacklist?

Is there a general bug for this blacklist?

---

### Post by -Robert- on 2010-04-24
> / The issue here is that some new software/drivers for Linux which do something called "kernel mode setting" for graphics cards haven't been sufficiently tested/developed for the particular cards with which you are having problems.  Specifying 'nomodeset' when the system boots basically tells the system to use an older set of software/drivers which does work (but may be slower or have some other issues that people would like to eliminate). Source: [http://wiki.sugarlabs.org/go/Nomodeset](http://wiki.sugarlabs.org/go/Nomodeset)

I don't know if the above explanation is correct, but I couldn't find much more about it.

---

### Post by Unicast on 2010-04-24
nomodeset did nothing for me.

---

### Post by dom96 on 2010-04-24
Well my graphics card is Radeon 4670, it worked fine though. Compiz worked very well.

---

### Post by phibxr on 2010-04-24
Nomodeset enabled me to boot. Nvidia Geforce 9600GT here, at least on this machine.

Still, people shouldn't be expected to have to pass a kernel option to boot the installation CD. This is a workaround, not a solution.

This was not an issue before Beta 2, by the way.

---

### Post by dom96 on 2010-04-25
Did someone already report this issue or should i ?

---

### Post by phibxr on 2010-04-25
> **dom96 said:**
> Did someone already report this issue or should i ?

I guess it's better that it gets reported one time too much than not at all. :)

---

### Post by Orographic on 2010-04-26
It worked for me with the nomodeset way mentioned above. This same system worked perfectly in Karmic though, so that is a bit weird...

Lucid still takes 25 seconds to boot though from log in, which was as slow as it was from Beta 1.

---

### Post by phibxr on 2010-04-26
Has a bug report been filed for this by someone?

I tried it on three other systems, with discs burned on two separate systems from three separate downloads.

Two out of the three systems would not boot unless I used the Nomodeset-option.

---

### Post by dom96 on 2010-04-27
[https://bugs.launchpad.net/ubuntu/+bug/570780](https://bugs.launchpad.net/ubuntu/+bug/570780)

Just reported it.

---

### Post by phibxr on 2010-04-27
> **dom96 said:**
> [https://bugs.launchpad.net/ubuntu/+bug/570780](https://bugs.launchpad.net/ubuntu/+bug/570780)

Just reported it.

Good, although I suspect it's far to late at this point. We'll see. :)

---

### Post by cariboo on 2010-04-27
I guess none of you needed to start up in safe graphics mode in previous versions?

Nomodeset just replaces that command.

---

### Post by Unicast on 2010-04-27
> **cariboo907 said:**
> I guess none of you needed to start up in safe graphics mode in previous versions?

Nomodeset just replaces that command.

Nope.

Beta2 worked like a charm, but the RC doesn't even boot without using the kernel option "i915.modeset=1"

Bug report here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/566379?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/566379?comments=all)

And the thread I was posting in: [http://ubuntuforums.org/showthread.php?t=1461675](http://ubuntuforums.org/showthread.php?t=1461675)

---

### Post by itsjustarumour on 2010-04-28
> **dom96 said:**
> [https://bugs.launchpad.net/ubuntu/+bug/570780](https://bugs.launchpad.net/ubuntu/+bug/570780)

Just reported it.
 
Is that the same thing as this one?

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/567899](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/567899)

Looks like they could do with some help troubleshooting there if anyone has the time and skills... would try and help out myself but I'm just dashing out to work! :|

---

### Post by phibxr on 2010-04-28
> **cariboo907 said:**
> I guess none of you needed to start up in safe graphics mode in previous versions?

Nomodeset just replaces that command.


I don't even need to do it in Beta 1. Only in Beta 2 and RC. I keep both Beta 1 and RC installed. :)

---

### Post by chris1379 on 2010-04-28
Anyone with this problem should check out the bugs mentioned above as well as [https://bugs.launchpad.net/ubuntu/+source/policykit-1/+bug/546992](https://bugs.launchpad.net/ubuntu/+source/policykit-1/+bug/546992)
Both bugs were solved for me by either inserting my removable floppy drive or disabling it in the BIOS. Anyone else have a floppy drive controller with no drive attached?

---

### Post by cambot on 2010-04-28
I too am getting this error...serious problems for a new release. I've been using Karmic with no problems, no problems with 10.04 Beta2 either. The release candidate throws this error....needs attention ASAP or people will ditch Ubuntu quick!

---

### Post by itsjustarumour on 2010-04-28
RE:

[https://bugs.launchpad.net/ubuntu/+s...ux/+bug/567899](https://bugs.launchpad.net/ubuntu/+s...ux/+bug/567899)

Looks like this is going to be added to the Lucid 10.04 Final Release Notes (and I quote):

"== Desktop installer sometimes crashes on startup ==

On some machines, the CD boot fails with the message "The installer encountered an unrecoverable error. A desktop session will now be run so that you may investigate the problem or try installing again." If you encounter this error, restart your computer with the CD inserted, press any key at the splash screen (when you see the keyboard icon at the bottom of the screen), and select "Try Ubuntu without installing". Once the desktop appears, use the "Install Ubuntu 10.04" icon to begin installing Ubuntu. (Bug:567899)"

... and the bug has then been marked as "Fix Released".

---

