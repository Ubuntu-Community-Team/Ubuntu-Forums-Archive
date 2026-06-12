---
title: "Printing largely but not entirely broken"
date: 2008-08-20
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by brm on 2008-08-20
I installed Intrepid Ibex Alpha 3 yesterday. Early experience suggests serious problems with printing. I take my Ubuntu in a Kubuntu flavour, but have also installed a complete Gnome desktop.

bruce@Xenophon:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu intrepid (development branch)
Release:        8.10
Codename:       intrepid
bruce@Xenophon:~$ uname -a
Linux Xenophon 2.6.26-5-generic #1 SMP Fri Aug 15 13:54:22 UTC 2008 x86_64 GNU/Linux
bruce@Xenophon:~$ dpkg -l  | grep kubuntu
ii  kubuntu-artwork-usplash                    1:8.10-2                                    kubuntu artwork for usplash
ii  kubuntu-default-settings                   1:8.10-2                                    Default settings and artwork for the Kubuntu desktop
 .... <snip ... and several other Kubuntu packages ...>

Several attempts to print from KDE applications have failed. The output begins with a few characters of high-order gibberish and continues with the text magnified about 11x. Have experienced this with printing from kate and from konqueror.

Have had the same problem with printing the CUPS test page from within Firefox ([http://localhost:631](http://localhost:631)) although other jobs from Firefox print normally.

On the other hand, jobs print normally from applications built with Gnome components, e.g. gedit, Firefox.

I am printing to an old HP laser printer which has only a parallel port. It is connected, however, to a hardware Ethernet print server and the printer is configured on my system as a remote LPD queue. As mentioned in the previous paragraph, all jobs go to the printer and those from Gnome applications print perfectly. However, the CUPS test page and KDE applications are killing many trees with much garbage.

Has anyone else had a similar experience? I would like to file a bug on Launchpad but am at a loss which package to file it against.

---

### Post by brm on 2008-10-06
I put up with this problem for six weeks.

Finally, I did a bare metal reinstall using a newly-burned copy of the Intrepid Ibex beta.

In this instance, printing works fine.

I can only assume that the ppd file which CUPS generated six weeks was broken in a way which can no longer be traced.

---

