---
title: "Sudo make install"
date: 2010-02-20
forum: Installation &amp; Upgrades
---

### Post by retsel25 on 2010-02-20
Hello, New to ubuntu 9.10 and trying to install a Gnome Menu.  I downloaded GnoMenu 2.4.1.tar.gz and I extracted the folder to my desktop. Now the instructions say "go there and run the following command: Sudo make install".  Thats where i'm stuck. Don't know how to do that. Please Help!!.

---

### Post by crlang13 on 2010-02-20
That's a command for the terminal (applications > accessories > terminal)

check out the beginner guide ([http://ubuntuforums.org/showthread.php?t=1052065](http://ubuntuforums.org/showthread.php?t=1052065)) before jumping right into the terminal though, especially with sudo commands

---

### Post by retsel25 on 2010-02-21
any other assistants? I went through the book and nothing really helped in what I'm trying to do. Here is what I'm trying to do: 

"SPICE UP GNOME MENU WITH GNOMENU", "Bored with Gnome’s drab and not so versatile menu, you gotta try GnoMenu. It is a consolidated menu for gnome that brings eye candy to the world of the Gnome menu’s. It is customizable and themable. It comes with several themes, and you can download many more from [http://gnome-look.org](http://gnome-look.org)

Installation is very simple, just download the source code of latest release from the developer’s website as given in the link above. Extract the download content, go to the directory where you extracted the content, there would be a folder called gnomenu, go there and run the following commad:

sudo make install"

Here is the link where I got this from - [http://www.hackourlives.com/?p=1244](http://www.hackourlives.com/?p=1244) 

I don't know how to make install?

---

### Post by crlang13 on 2010-02-21
I see...

So, you still want to open the terminal as I said above.

Then, in the terminal, you need to change the directory to the directory you saved the package.

Let's say you saved it in documents the command to change there would be:

cd ~/Documents 

if it's in a folder called "stuff" within Documents, then:

cd ~/Documents/stuff

The default directory for when you first open the terminal is /home/yourname, so if you already saved there, you'll be fine.  Be aware as well that file names are case sensitive.

so if I were you, I'd throw the gnomenu folder into /home/yourgame (just using the gui).  Then in the terminal type:

cd ~/gnomenu
sudo make install

you'll be prompted for your sudo password after this.

goodluck

---

### Post by oldos2er on 2010-02-21
Gnomenu is in the repositories: ```
sudo apt-get update && sudo apt-get install gnomenu
```

---

### Post by retsel25 on 2010-02-23
thank you crlang13, exactly what I wanted. I got it installed. And thank you to oldso2er for that response, but that did not work for me. But crlang13's did. solved!!

---

