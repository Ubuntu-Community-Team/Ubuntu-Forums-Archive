---
title: "Black desktop in Ubuntu 18.04 (SOLVED)"
date: 2018-08-29
forum: Installation &amp; Upgrades
---

### Post by padaenriqueidey on 2018-08-29
Hello, good Having installed Ubuntu 16.04, as I installed in a forum, able to upgrade to Ubuntu 18.04. The thing is that my 32-bit PC does not allow the installation of Ubuntu 18.04 64-bit, but an update. But the desktop only shows the doc and the task panel above. Do not allow the files or folders to be blank, or download the text and background to be black without being able to change the color or put a desktop background.
Greetings.

---

### Post by DuckHook on 2018-08-29
I'm not sure that I completely understand you, but if it is what I think, then your problem is a tough one. Essentially, what you've done (whether intentionally or not) is create a sort of Frankenstein's monster. Since Canonical made the decision to stop supporting 32-bit, by upgrading into 18.04, your workaround basically horks together castoff limbs and spare organs to create what is essentially a highly customized GUI environment. Canonical cannot support it and, for what it is worth, I cannot even reproduce it.

While I do run 32-bit Linux machines, they are all still on Xenial and are exclusively CLI since they are acting as servers. I have found that the best way to keep 32-bit machines relevant is to reposition them as servers. By eliminating the GUI, you simplify things to the point where a 32-bit mini.iso will install.

If you must run 32-bit GUI, then the best temporary solution may be to reinstall 32-bit Xenial. There is still almost 3 years of life left in Xenial so you will continue to get support. Further alternatives are to leave the Ubuntu world and use different distros that still support 32-bit. If there are Forum members who run 32-bit Bionic, hopefully they can offer some further guidance.

---

### Post by padaenriqueidey on 2018-10-20
Black desk, the dock and the panel I see them and I can use them.

You enter as superuser
sudo its

You update the system, update more important packages and install the ubuntu desktop.
apt update && apt dist-upgrade && apt install ubuntu-desktop

Restarts
reboot
Now you can see the bottom of the desk.

---

### Post by wildmanne39 on 2018-10-20
Hello padaenriqueidey to post images please use the attachment facility by clicking on the paperclip and in your case the links do not work and it shows your username which I believe is a security issue, I did copy and paste your link into google search and it displayed many images for your desktop by your username but there is no url for your images so there is no way for them to be displayed as you intended.

---

### Post by padaenriqueidey on 2018-10-23
But what is true that the problem I have solved, I see the wallpaper.

---

### Post by wildmanne39 on 2018-10-23
It is hard to follow what you are saying but if you solved this issue please use thread tools at the top of the page to mark the thread solved and please post your solution so the whole community can benefit from your experience.

Thanks

---

