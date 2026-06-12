---
title: "How to NOT run Gnome on Ubuntu startup"
date: 2008-05-01
forum: Installation &amp; Upgrades
---

### Post by burtram on 2008-05-01
Good afternoon,
I am not much of a Linux guru and am finding it difficult to identify the simplest way to stop the Gnome GUI from loading on my Ubuntu server when it starts up. (I do want the ability to run Gnome for when I am stuck on how else to do something using the command line, so I don't want to remove it, and it seems that run levels aren't supported the same as in RedHat and Suse.) Ideally the solution would be the most generalisable one to other similar situations and/or distributions.

Sorry for such a basic question, but an reasonably extensive trawl of the web has led me to many places, none of which I am sure is the best way to achieve this.

Many thanks.

---

### Post by dstew on 2008-05-01
The quick and dirty way is to boot into single mode (Recovery mode boot, should be a grub menu item). This boot stops at run level 1, and I think the Gnome display manager (GDM) comes in later.

The more sophisticated way would be to use a program like rcconf to re-configure the startup scripts. I think you can use this program from a command line, and prevent the xserver or GDM from loading at startup. Here is a [web site that shows some rcconf screenshots]("http://www.debianhelp.co.uk/initscripts.htm"). There is also a graphical tool that does the same thing, and I think it is System --> Services (not at my Linux computer so I am not sure).

---

### Post by yyyc186 on 2008-05-01
When your system first boots to a username prompt, you will find an "options" item in the lower left hand corner.  click on it.  One of the options is "session select" or "select session", can't remember right now.

After you log in, you will see a message box asking if you want to change your default or just for this session.  Change for default.

Now you will be running KDE, a much more robust and well thought out desktop.

I too cannot tolerate Gnome.  I gave it a year, but it seems to be developed by creatures who think running water and indoor plumbing are luxuries society can do without.

---

### Post by burtram on 2008-05-02
Thanks for this. In the GUI I went to System, Administration, Services and unticked the 'Graphical login manager' option. Now I login at the CLI and can run Gnome if needed using startx. Just what I wanted!

---

