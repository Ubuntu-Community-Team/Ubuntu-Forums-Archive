---
title: "Gnome not working properly"
date: 2010-02-16
forum: Installation &amp; Upgrades
---

### Post by gwu777 on 2010-02-16
Hello everyone, yesterday I have updated my ubuntu to the following kernel: 2.6.31-20. There has been several other update such as compiz that I do not have installed!!!

Anyway, now I gnome doesn't work properly - at least I think it is Gnome, I cannot switch between windows, I do not have the bar on top with the cross and all I only have one desktop loaded out of 4 and the computer is continuously working.

What should be my next step?

I have restarted with the older kernel and it is still the same problem...

Thank you for help

---

### Post by dE_logics on 2010-02-16
> There has been several other update such as compiz that I do not have installed!!!

You have it installed in Ubuntu by default.

It appears there's something wrong with the window manager...maybe compiz conflicts with it.

So right click on the desktop, go to the last tab (visual enhancement...something like that) and select "none". At times compiz can conflict with the existing window manager.

---

### Post by gwu777 on 2010-02-16
> **dE_logics said:**
> So right click on the desktop, go to the last tab (visual enhancement...something like that) and select "none". At times compiz can conflict with the existing window manager.

The visual effect are already to none!!!

---

### Post by gwu777 on 2010-02-17
Is there anything I can do to know more what the problem is and how to fix it? Any log I can check???

---

### Post by llawwehttam on 2010-02-17
If you have graphics drivers from nvidia's website installed then re-install them then re-enable desktop effects.
If not it is somthing else graphics related.

---

### Post by macabrem on 2010-02-17
I had this same problem.  Although, the only thing I could connect my problem to was that I installed the Enlightenment DE and then uninstalled it (through Synaptic).  Then Gnome was broke.

I tried to reinstall Compiz and various Gnome files to no avail.  I ended up backing up my data to an external and then reinstalling my OS (I use Mint).

---

### Post by gwu777 on 2010-02-18
> **llawwehttam said:**
> If you have graphics drivers from nvidia's website installed then re-install them then re-enable desktop effects.
If not it is somthing else graphics related.

This is w&#295;a&#359; I &#295;ave done, i have uninstalled the nvidia driver and now everything is back. I guess when it updated the kernel and co, something got corrupted. I haven teinstalled the drivers as I don intend to use the extra graphics, I like it to be as fast as possible. Is there any reason why I should use the nvidia driver if I am happy without it?

---

