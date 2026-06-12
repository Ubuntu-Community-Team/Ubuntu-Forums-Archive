---
title: "No X, or atleast not working proberly"
date: 2009-07-31
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by thepanu on 2009-07-31
I installed alpha2 a while back today was first time I ran any updates in this machine (Samsung NC20 netbook).

Alpha 2 worked generally well.

Now after update I can't get in to X, no login screen nothing. Only thing I am getting is screen changing from black to white to red to green to blue to horizontal b/w gradient to vertical b/w gradient. And this cycle continues indefinately.

I did't get warning about partial update, but chose to ignore the warning.

I tried reinstalling gdm, reinstalling ubuntu-deskop, installing xubuntu-deskopt and kubuntu-desktop and they all gave same kind of error.

I am able to switch tty.

Any ideas on how to proceed, search didn't yield any reports on similar problems.

---

### Post by psyke83 on 2009-08-01
It may be modesetting.

Boot with the boot option "nomodeset" to see if it helps.

---

### Post by thepanu on 2009-08-01
Thanks for the tip, but that didn't change anything.

Assuming that I did it correctly.

In grub menu I edited options with 'e' and added row 'option=nomodeset' and hit ctrl-x to boot.

---

### Post by Yofel on 2009-08-01
I think it should have been just 'nomodeset' without the option= thing.
Another way to disabled KMS for intel cards would be 'i915.modeset=0' (The message that the option will be ignored is ok, the kernel ignores it but passes it to the driver later on.)

---

### Post by jerrylamos on 2009-08-01
Various video graphics chips are having various problems.  I don't know which one you have.  Boot in recovery mode, on the recovery menu go down to root shell prompt and try:
lspci | grep VGA
to see which chipset you have.  If having X problems its always useful to put this in your comment.

If you have an intel video graphics chip, then see thread
[http://ubuntuforums.org/showthread.php?t=1228577](http://ubuntuforums.org/showthread.php?t=1228577)

If you have an ATI radeon chipset, then there was an update today which might or might not help.  From the recovery mode root prompt do
dhclient
to get the internet then
apt-get update
apt-get dist-upgrade
Y

then reboot....

Good luck, Jerry

---

