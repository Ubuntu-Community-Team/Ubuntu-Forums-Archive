---
title: "not so Easy Ubuntu"
date: 2006-03-19
forum: Installation &amp; Upgrades
---

### Post by cab1024 on 2006-03-19
I get this error trying to install a bunch of stuff with today's Easy Ubuntu installer. So far nothing has actuallybeen installed by Easy Ubuntu.

(synaptic:10902): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

(synaptic:10902): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

chuck@saltydog:~/easyubuntu$ Synaptic exited with return code =  0
<bound method Do.icons of <__main__.Do instance at 0xb6f4156c>>
Gnome-Terminal exited with return code =  0

Any ideas what to do?

---

### Post by Vietman on 2006-03-19
-- BUMP --

me too.

I'm trying out EasyBreezy for that very reason.

---

### Post by cotcot on 2006-03-19
I do not know the reason of the error. I posted the same problem some time ago and there were no tips to eliminate the null errors. Although the NULL errors synaptic functions by me, so I do not care about the errors. The reason that your synaptic does not open has nothing to do with the NULL errors I think. Have you tried to start synaptic in terminal with the command "sudo synaptic" ?
If you need to install something you can also use "apt-get install packagename" in terminal. It happens that synaptic has problems in accessing the repositories at the same moment that there is no problem with apt-get. Dependencies are installed automatically in both ways.

---

### Post by cab1024 on 2006-03-20
[QUOTE=cotcot]I do not know the reason of the error. I posted the same problem some time ago and there were no tips to eliminate the null errors. Although the NULL errors synaptic functions by me, so I do not care about the errors. The reason that your synaptic does not open has nothing to do with the NULL errors I think. Have you tried to start synaptic in terminal with the command "sudo synaptic" ?[/QUOTE]
I switched to EasyBreezy and it worked much better. I still get the NULL errors, but at east the software gets installed in the end. With Easy Ubuntu, the process continued through the errors and seemd to accomplish things, but nothing ever showed up in the Menus nor could I find anything with searches.

EasyBreezy seemed to do the trick. Too bad, because Easy Ubuntu has a much nicer interface.

I still can't see the video on webcam I want though:
[http://www.mavsurfer.com/main_page/](http://www.mavsurfer.com/main_page/)

Does Ubuntu only handle Java 1.4? Not up to 5.0 as this seems to require? But that is another topic I suppose.

Thanks for the EazyBreezy suggestion.

---

