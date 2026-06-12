---
title: "i have a problem with IEs4linux for ubuntu 9.1.0"
date: 2009-12-17
forum: Installation &amp; Upgrades
---

### Post by aviv4000 on 2009-12-17
Hi, 
I'm very new in Ubuntu (2 days)
I'm trying to insall IEs4linux but its not working
(i need it for some web sites which are not supporting firefox)
i followed the instructions in: [http://www.psychocats.net/ubuntu/ies4linux](http://www.psychocats.net/ubuntu/ies4linux)
everything worked up to the last step where i got the window to work and then it became empty...

and the terminal states:

IEs4Linux 2 is developed to be used with recent Wine versions (0.9.x). It seems that you are using an old version. It's recommended that you update your wine to the latest version (Go to: winehq.com).

/home/aviv7000/ies4linux-2.99.0/ui/pygtk/ies4linux-gtk.py:268: GtkWarning: gtk_text_layout_real_invalidate: assertion `layout->wrap_loop_count == 0' failed
  self.textbuffer.insert_with_tags(self.textbuffer.get_end_iter(), line, tag)



[IMG]http://ubuntuforums.org/home/aviv7000/%C3%97%C2%A9%C3%97%C2%95%C3%97%C2%9C%C3%97%C2%97%C3%97%C2%9F%20%C3%97%C2%A2%C3%97%C2%91%C3%97%C2%95%C3%97%C2%93%C3%97%C2%94/Screenshot.png[/IMG]
I upgraded yesterday to Ubunto 9.1.0
please help!!!
:)

Sean

---

### Post by aysiu on 2009-12-18
Even though [this](http://www.susegeek.com/internet-browser/run-internet-explorer-in-opensuse-103-using-ies4linux/) is for OpenSuSE, I think it should apply to Ubuntu as well: > Sometimes, you might end up with the following error..but don&#8217;t panic: ```
IEs4Linux 2 is developed to be used with recent Wine versions (0.9.x). It seems that you are using an old version. It&#8217;s recommended that you update your wine to the latest version (Go to: winehq.com). No user interface available. Use command-line ies4linux or install pygtk. Details: http://www.tatanka.com.br/ies4linux/page/No_GUI IEs4Linux 2 is developed to be used with recent Wine versions (0.9.x). It seems that you are using an old version. It&#8217;s recommended that you update your wine to the latest version (Go to: winehq.com). 
``` This is a known problem caused by GTK. Simply run the installer without the GUI as follows: ```
saihari@OpenSuse:~/ies4linux-2.99.0.1> ./ies4linux &#8211;-no-gui
``` That installs ies4linux on your linux under your home directory.

---

### Post by aviv4000 on 2009-12-19
> **aysiu said:**
> Even though [this]("http://www.susegeek.com/internet-browser/run-internet-explorer-in-opensuse-103-using-ies4linux/") is for OpenSuSE, I think it should apply to Ubuntu as well:

1. thank you very much!
2. I tried it but it didn't work...

---

### Post by nexx on 2009-12-21
Thanks a lot, I was having the same problem.  I also folowed the advicre on the ubuntu french forum and disabled compiz during installation as it seems that compiz also can bug ie4linux installation. And for the first time even the png render well on ie6.

If the png do not show corectly, I also found that console:lolflag: command on the french forum:
WINEPREFIX="$HOME/.ies4linux/ie6" wine regsvr32 "C:\windows\system32\pngfilt.dll"
:guitar:

---

