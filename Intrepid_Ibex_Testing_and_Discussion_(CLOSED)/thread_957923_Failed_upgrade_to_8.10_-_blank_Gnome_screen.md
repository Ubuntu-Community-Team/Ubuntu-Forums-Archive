---
title: "Failed upgrade to 8.10 - blank Gnome screen"
date: 2008-10-24
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by tandlj on 2008-10-24
After upgrading from 8.04 to 8.10 with the Update Manager, the screen which is displayed after logging into Ubuntu remains blank (but has the usual Gnome desktop colour).

I remember being asked to keep or overwrite a file called 'gnome.defaults' or similar during the install and choosing 'overwrite'. Is this the cause of the failed install? Can it be fixed? (I have 'home' in a separate partition.)

---

### Post by 4kfooler on 2008-10-24
Me 2............

---

### Post by jerrylamos on 2008-10-25
In my case, IBM Thinkpad R31 Intel Celeron 32 bit, Intel graphics those symptoms are caused by compiz, the code that does Gnome Desktop "eye candy" by doing fancy tricks with the graphics hardware and drivers.

One way to check is to try Xubuntu CD Live which doesn't use compiz.

My Ubuntu workaround, see Launchpad Bug # 259385 is to:
Boot in rescue mode
on the pop-up window:
choose Root prompt
sudo apt-get remove compiz
sudo apt-get remove compiz-core
exit
resume normal boot

If that works you're O.K. except for missing the "eye candy" special effects.

If you want to put compiz back in, repeat the steps with install instead of remove, however you may well need a working internet connection.
Just after choose Root prompt add:
sudo dhclient
ifconfig
to see that the network connection is working, then do the above steps with install instead of remove.

Jerry

---

