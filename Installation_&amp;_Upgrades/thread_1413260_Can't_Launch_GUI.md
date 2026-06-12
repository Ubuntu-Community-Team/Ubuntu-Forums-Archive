---
title: "Can't Launch GUI"
date: 2010-02-22
forum: Installation &amp; Upgrades
---

### Post by goatwhore on 2010-02-22
I'm have much computer experience but am new to Ubuntu.

I typed in sudo apt-get install ubuntu-desktop and it tells me it's already installed. Good. So it should work. I type sudo/etc/init.d/gdm start and the screen goes blank for 8 seconds three times in a row and then back to the command line. I have also tried gdm start without the path before and it says GDM already running. Aborting!

I have 8.10 and it's a valid disk (no errors).

Can someone help please?

---

### Post by byStanderone on 2010-02-22
...kindly elavorate a little more for us to have a clearer picture of your install.

---

### Post by goatwhore on 2010-02-22
Ok I have a Toshiba Satellite P200 laptop with Windows 7 installed. I don't want to wipe 7 off until I am absolutely sure Ubuntu will work for me. What information do you need?

---

### Post by byStanderone on 2010-02-22
...you've mentioned command line, do i get it right that you are booted in a console? somehow it seems that you've installed the server distro, correct me if am wrong.

---

### Post by goatwhore on 2010-02-23
Hey I posted the question in a couple other forums and it turns out that after installing Windows 7 on another partition guess what Windows decided to do? So I have no boot loader and 7 is loaded by default.

So what I have been doing is booting from the install CD every time in order to get to my Ubuntu OS and that was why I couldn't start the GUI.

[http://www.linuxquestions.org/questions/linux-newbie-8/cant-launch-gui-from-command-line-790825/#post3872853](http://www.linuxquestions.org/questions/linux-newbie-8/cant-launch-gui-from-command-line-790825/#post3872853)

---

### Post by byStanderone on 2010-03-06
...sorry, haven't gone back to you sooner, i hope you'd got the fix to your ubuntu install. re-read your thread, and it seems you have to re-install grub in the ubuntu partition itself since it was wiped out by the other 'os'.

---

