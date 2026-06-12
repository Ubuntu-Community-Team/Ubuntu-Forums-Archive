---
title: "Problem with gflrx driver recognize my screens as unknown"
date: 2010-04-12
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by aviramof on 2010-04-12
i am currently using latest 32 kernel i removed and reinstall gflrx driver now everything is working fine compiz as well but i still have an old problem i think it had something to do with the kernel 32 that he detect all my screens as unknown in monitors why is that and how can i fix it?

this is one of the reasons i use kernel 2.6.33 if not the main reason by the way.

---

### Post by aviramof on 2010-04-13
doesn't any one have an answear?
i have just reinstalled 2.6.32-20 and everything is working fine again the fglrx compiz and etc so why when i check in gnome-display-properties it display me my screens as unknown?

---

### Post by Cillean on 2010-04-13
My screens are also referred to as "unknown", but I don't understand why this is such a big problem for you - all the settings still work. And if you really need to see the name of your screens, just use the Catalyst Control Center where the recognition works fine.

---

### Post by aviramof on 2010-04-13
if it doesn't recognize it well it mean he's not necessary know how to work well with it and 
this is the kernel itself that doesn't recognize it the fact that Catalyst Control Center does is irrelevent for the behavior of the kernel.

---

### Post by Cillean on 2010-04-13
This does not mean that Ubuntu doesn't know how to work well with the monitor - obviously, you're getting an image on your screen. It's just that it's not getting the name because it's not in the detection list (see also [http://ubuntuforums.org/showthread.php?p=8926208#post8926208]("http://ubuntuforums.org/showthread.php?p=8926208#post8925980")). And if your screen is working fine and you can do everything you need to, I don't think it's an important problem - at least it isn't important enough for me to switch to another kernel. By the way, I don't think this is a kernel-specific problem, afaik the detection is done by Gnome or X, but not the kernel (correct me if I'm wrong).

---

### Post by aviramof on 2010-04-13
i don't think your wrong but it only happen if i use fglrx driver if i use xorg is OK and i have three screen one computer screen and two TV's and all of them are recognize by xorg in gnome-display-properties but not when i use fglrx is that sound reasonable to you?

---

### Post by Cillean on 2010-04-13
Yes, that's reasonable, gnome-display-properties doesn't seem to work with fglrx. I don't exactly know what the problem is, but I guess that it cannot be fixed as the problem will be in the proprietary driver which cannot be changed by the Ubuntu developers. I suppose we'll have to live with that little annoyance ;)

---

### Post by aviramof on 2010-04-14
i don't remeber heaving that little problem with ubuntu 8.10

---

