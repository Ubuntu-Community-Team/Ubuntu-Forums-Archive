---
title: "cdrom no longer recognized"
date: 2008-10-19
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by marttali on 2008-10-19
Hi,

k3b reports "No CD/DVD writer found.
K3b did not find an optical writing device in your system. Thus, you will not be able to burn CDs or DVDs. However, you can still use other K3b features like audio track extraction or audio transcoding or ISO9660 image creation."

Tried with kdesudo, same thing

If i insert a cd/dvd nothing happens. Dolphin doesn't seem to know that there's cd/dvd also. My useraccount belongs to groups cdrom and plugdev.
it used to work about week ago, so some updates broke it.
So what's the fix ?

---

### Post by Doctoxic on 2008-10-19
maybe have a similar problem  (all worked fine before i upgraded)

if i manually open the DVD drive it immediately closes so is unusable

and in the top system tray bar it the button to mount/unmount isn't there

what sort of drive do you have - only mine is SATA and i wonder if this is causing a problem

doc

---

### Post by marttali on 2008-10-19
it's IDE
Anyone ?

---

### Post by omgbots on 2008-10-21
No additional information other than to say my IDE burner is no longer working either.  Obviously an issue with a recent upgrade.

---

### Post by Hairy_Palms on 2008-10-21
confirmed here too, tho it still reports my 2nd Hard Disk as a Picture CD XD

---

### Post by marttali on 2008-10-22
i would like to add there is no sign of cdrom in either lshw or hwinfo or hal-device-manager. Atleast i cant see it.
I tried in k3b to add readonly and writeable devices- /media/cdrom -"couldn't find..." was the response.
So which logs should i check for errors or can I reconfigure something ? Kernel is the latest.
I also tried to boot with earlier kernels (.4 and .6), nothing.

---

### Post by pulpo69 on 2008-10-22
my cdrom/dvddrive don't work properly. can't eject (only a message appears:
another application prevents to unmount your cdrom-drive).
cannot burn cd with brasero and with k3b only sometimes.
sometimes i can eject the cdrom but it opens and closes again in the same moment.
can anyone publish the line fom fstab who has working cdrom-drive?
thanks in advance.

---

### Post by marttali on 2008-10-22
My problem is solved !
Solution - changed the cdrom jumper settings from slave to master. Cdrom is IDE. So I have 2 masters now- SATA HDD and IDE cdrom. That's it.
8.04 didn't have problem with it, 8.10 doesn't like it apparently.

---

