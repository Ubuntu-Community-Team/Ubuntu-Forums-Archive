---
title: "Plasma crash"
date: 2009-02-22
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by HoellP on 2009-02-22
Hey folks
I installed some Updates today on Kubuntu Jaunty (VirtualBox VM) and since then plasma crashes on login, when the loading animation is finished. I get stuck with kdm's background and the mousepointer. I can use Alt+F2 to start konsole and when I try to start plasma I get this error: [http://pastebin.com/f1d0cd4f6](http://pastebin.com/f1d0cd4f6)
Anyone got an idea what I could try besides waiting for an update?
Thanks

---

### Post by inportb on 2009-02-22
Hm... my Plasma crashed yesterday with the same symptoms and I realized that a plasmoid was probably acting up. So I removed the plasmoid config file **~/.kde/share/config/plasma-appletsrc** and it started working again.

Today I tried adding the Quick Launch widget and that would crash Plasma every time. Do you have this widget?

---

### Post by HoellP on 2009-02-22
Deleting plasma-appletsrc fixed the error, but after a reboot every widget seems to work...
So everything back to normal, thanks.

---

### Post by daflame on 2009-03-07
I have been experiencing a similar problem with Intrepid, but removing plasmarc doesn't solve the problem, neither does removing the whole .kde config directory.

---

### Post by paracetamolo on 2009-03-07
Same here, removed the whole .kde and plasma still doesn't start at login.

---

### Post by utkjamie on 2009-03-13
No solution?

---

