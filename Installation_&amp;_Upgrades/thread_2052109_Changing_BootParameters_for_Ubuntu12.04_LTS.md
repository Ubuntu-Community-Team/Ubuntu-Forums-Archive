---
title: "Changing BootParameters for Ubuntu12.04 LTS"
date: 2012-09-02
forum: Installation &amp; Upgrades
---

### Post by jkasai on 2012-09-02
Hi,

Can I please ask for some help regarding making permanent changes to bootparameters? Just installed Ubuntu! Woohoo!...still not sure how to operate, etc.

Installed Ubuntu from a CD, but had to change "quiet splash--" to "irqpoll".
On [https://help.ubuntu.com/community/BootParameters](https://help.ubuntu.com/community/BootParameters) it says that I "need to make permanent changes in the file /boot/grub/menu.lst after the installation has completed."
...Not sure how.

Also having problems with finding my wireless.
Looked into "Network" but it only gives me "Wired" and "Network proxy".
Can't find "Wireless" or anything :"(

I would be really and truly grateful if you could help me out!!

Thank you in advance!

M

---

### Post by Bashing-om on 2012-09-02
jkasai;

  Hi ! welcome to the forum.

Firstly: /boot/grub/menu.lst; has been depreciated for the longest time. What version are you attempting to boot?

If you are attempting to install an old version, be advised a lot of changes have transpired, hardware recognition in particular, in latter versions. It is strongly advised to try 12.04 (the current long term support) .

Confirm your version and you will be advised on/how to edit (etc/default/grub), if that remains your desire.

[INDENT]hth <==BDQ
[/INDENT]

---

### Post by jkasai on 2012-09-02
Hello!

Thank you so so very much for your reply! :D

I installed the Ubuntu 12.04 LTS...

---

### Post by jkasai on 2012-09-02
> **Bashing-om said:**
> jkasai;

  Hi ! welcome to the forum.

Firstly: /boot/grub/menu.lst; has been depreciated for the longest time. What version are you attempting to boot?

If you are attempting to install an old version, be advised a lot of changes have transpired, hardware recognition in particular, in latter versions. It is strongly advised to try 12.04 (the current long term support) .

Confirm your version and you will be advised on/how to edit (etc/default/grub), if that remains your desire.
[INDENT]hth <==BDQ
[/INDENT]

Sorry, I'm going to sound like a noob but 12.04 is a version right?
As in, did I answer your question right? Woops :$ haha sorry

---

### Post by Bashing-om on 2012-09-02
jkasai; 
Yeah, now we are cooking!


ok all there is to it is open a terminal ctl+alt+t,
1st make backup of grub file
```
sudo cp /etc/default/grub /etc/default/grub.orig
```enter password in terminal
then in terminal to load the text editor enter:
```
gksudo gedit /etc/default/grub
```be advised that gksudo = graphical sudo required method for all graphical applications from terminal.
input password in pop-up window
The text editor loads up the grub file; in this file locate the line that is similar to this one:
linux /boot/vmlinuz-3.2.0-24-generic root=UUID=dbd69ed2-530c-4409-8f5a-a3f1ea41fc67 ro quiet splash
now make your edits  as used in the kernel boot line and save and exit gedit.

to write the changes to the real config file run:
```
sudo update-grub
```from the terminal ..input password at the terminal prompt.

reboot and should be good to go.

on the wireless..if still having a problem, please open up another thread. (1 fault to the thread to aid those searching for solutions).[INDENT]regards <==BDQ
[/INDENT]

---

### Post by jkasai on 2012-09-02
[QUOTE=
The text editor loads up the grub file; in this file locate the line that is similar to this one:
linux /boot/vmlinuz-3.2.0-24-generic root=UUID=dbd69ed2-530c-4409-8f5a-a3f1ea41fc67 ro quiet splash
[/QUOTE]

Hey! Thank you for such a speedy response! I really appreciate it!

Unfortunately, I can't find a line similar to the one above...
There's one that says:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=" "

:"( not sure what to do.

Does the Command Prompt option that you wrote about below do the same thing as what's being done here on the grub?

Thank you so much for your help btw!! Totally appreciate it! :)

---

### Post by jkasai on 2012-09-02
Bashing om;

Sorry! Forgot to mention that under the two GRUB_CMDLINE_LINUX lines,

There's:

"Uncomment to enable BadRAM filtering, modift to suit your needs

Uncomment to disable graphical terminal (grub-pc only)

Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux

Uncomment to disable generation of recovery mode menu entries

Uncomment to get a beep at grub start"

etc.

---

### Post by Bashing-om on 2012-09-02
jkasai;

  My apologies... I indicated the line from a different file in my haste. The line you are referencing is correct (I verified it with my installation's grub file) . The one with quiet splash.

Again, sorry for the delay my error caused.

[INDENT]press on! <==BDQ
[/INDENT]

---

### Post by jkasai on 2012-09-02
> **Bashing-om said:**
> jkasai;

  The line you are referencing is correct (I verified it with my installation's grub file) . The one with quiet splash.



Thank you!!! 
So I'll just change that to GRUB_CMDLINE_LINUX_DEFAULT="irqpoll"
?

:D thank you!!!

---

### Post by Bashing-om on 2012-09-02
that will work.... however if you delete the quiet and splash items you boot with the boot messages displayed (and shutdown too) ,,, and boot to a login terminal rather than the gui login. Keep this in mind, but for now I suggest that you leave both quiet and splash in that line too.

remember to save and run sudo update-grub to write the change.

[INDENT]BDQ
[/INDENT]

---

### Post by jkasai on 2012-09-03
Thank you so so much Bashing-om!!! 
You're the best!

Would it be okay for me to ask you about the wireless problems I'm having too?
Ofcourse in another thread. :)

Thank you so much again!

M

---

### Post by Bashing-om on 2012-09-03
Thanks!
The other issue will be addressed in another thread. Just start a new one and me or some one else will pick it up...

[INDENT]happy Ubuntuing ! <==BDQ

[/INDENT]

---

