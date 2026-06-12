---
title: "Jaunty notifications stop working"
date: 2009-03-30
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by pjalegria on 2009-03-30
Hi

After today updates jaunty notifications stop working, anybody else...

---

### Post by Chemical Imbalance on 2009-03-30
I'm up to date on jaunty and they are still working fine here.

edit:  I'm on 64 bit also

---

### Post by traxxas on 2009-03-30
I just updated today and osd-notify crashes on startup, tries to restart itself and eats all my cpu.  I just killed it and went about my normal work.  So I can say me too with this problem, amd64 btw.  I found the log entries for the segfault.

```

Mar 30 10:45:26 wobbly kernel: [  255.983296] notify-osd[4774]: segfault at 58 ip 00007ffcff192f50 sp 00007fff0a259b80 error 4 in libX11.so.6.2.0[7ffcff149000+102000]
Mar 30 10:45:32 wobbly kernel: [  261.268869] notify-osd[4910]: segfault at 1720000012a ip 00007f472d14df50 sp 00007fff38213f50 error 4 in libX11.so.6.2.0[7f472d104000+102000]
Mar 30 10:45:32 wobbly kernel: [  261.616343] notify-osd[4916]: segfault at 78 ip 00007f3a06ce8f50 sp 00007fff11db1af0 error 4 in libX11.so.6.2.0[7f3a06c9f000+102000]
Mar 30 10:45:32 wobbly kernel: [  261.935434] notify-osd[4919]: segfault at 78 ip 00007f7310707f50 sp 00007fff1b7d0510 error 4 in libX11.so.6.2.0[7f73106be000+102000]
Mar 30 10:45:33 wobbly kernel: [  262.291837] notify-osd[4924]: segfault at a ip 00007f7841d9ff50 sp 00007fff4ce66ba0 error 4 in libX11.so.6.2.0[7f7841d56000+102000]
Mar 30 10:45:33 wobbly kernel: [  262.592652] notify-osd[4930] general protection ip:7f1a8cae8f50 sp:7fff97bb18f0 error:0 in libX11.so.6.2.0[7f1a8ca9f000+102000]
Mar 30 10:45:33 wobbly kernel: [  262.912187] notify-osd[4934]: segfault at 100000b ip 00007f2cb86e3f50 sp 00007fffc37ac4f0 error 4 in libX11.so.6.2.0[7f2cb869a000+102000]
Mar 30 10:47:13 wobbly kernel: [  362.526899] notify-osd[5070]: segfault at 148 ip 00007fe6a9cebf50 sp 00007fffb4db2af0 error 4 in libX11.so.6.2.0[7fe6a9ca2000+102000]
Mar 30 10:47:13 wobbly kernel: [  362.832929] notify-osd[5073] general protection ip:7f2498a51f50 sp:7fffa3b1a860 error:0 in libX11.so.6.2.0[7f2498a08000+102000]
Mar 30 10:47:14 wobbly kernel: [  363.158620] notify-osd[5076]: segfault at 78 ip 00007f5ec65aff50 sp 00007fffd16783b0 error 4 in libX11.so.6.2.0[7f5ec6566000+102000]
Mar 30 10:47:26 wobbly kernel: [  375.926587] notify-osd[5091]: segfault at 706f746b7b ip 00007f7976c23f50 sp 00007fff81ceca30 error 4 in libX11.so.6.2.0[7f7976bda000+102000]
Mar 30 10:47:27 wobbly kernel: [  376.235439] notify-osd[5094]: segfault at 58 ip 00007f4e1f1d9f50 sp 00007fff2a29ffe0 error 4 in libX11.so.6.2.0[7f4e1f190000+102000]

```

---

### Post by Hakkatuka on 2009-03-30
Do you have wallpaper plugin enabled in Compiz? It seems to hide the notifications for me, it worked fine just yesterday.

---

### Post by pjalegria on 2009-03-31
I dont have compiz enable, i have netbook remix, and still no notifications

Help, please

---

### Post by kaibob on 2009-03-31
What kind of notifications is this supposed to provide? 

If I change the volume level, a black box with a speaker appears in the upper right-hand corner of the screen. But, I don't get printer or network outage or system notifications of any kind? I'm not using compiz.

---

### Post by pjalegria on 2009-03-31
I dont have any...

---

### Post by kaibob on 2009-03-31
I did a bit of research and have what I hope is a better understanding of the jaunty notification system.

Apparently the indicator applet is actually a messaging and evoluton indicator applet. I don't use messaging or evolution, so I will remove this applet from startup programs and the panel.

The "notification area" is standard and contains network icon and other information. This, of course, needs to be retained.

The notifications-preferences menu is under *System > Preferences*. I couldn't find this because it was hidden and had to use "Edit Menus" to show it in the menu. The actual notifications are about volume levels, network outages, email, and the like. The volume and network-outages notifications do appear on my machine.

---

### Post by traxxas on 2009-03-31
> **pjalegria said:**
> I dont have compiz enable, i have netbook remix, and still no notifications

Help, please

I also don't have compiz enabled, I'm using metacity with its own compositing.

---

### Post by shu on 2009-04-01
Doesn't work for me. Notifications show up as small windows in the middle of the screen. :-/

---

### Post by mnk on 2009-04-18
For me the notifications appear only for pidgin but it looks nothing like the flash video on Mark Shuttleworth's site.

Anyone know how to get the black notifications working?

How can I test it? How do I know it is working!?

Thanks in advance for any help

---

### Post by Dread Knight on 2009-04-21
Same issues here...

---

### Post by pokogr on 2009-04-22
mine too :(

---

### Post by pokogr on 2009-04-22
> **pokogr said:**
> mine too :(

Never mind. 

For those having the old notifications back:
I had the awn-notification-daemon activated through awn properties and after yesterday's update I lost the Jaunty's default. If you disable the awn's notification daemon you'll get the old ones back.

---

