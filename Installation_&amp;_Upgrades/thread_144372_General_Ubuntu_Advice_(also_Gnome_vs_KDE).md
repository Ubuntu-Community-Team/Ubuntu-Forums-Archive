---
title: "General Ubuntu Advice (also Gnome vs KDE)"
date: 2006-03-14
forum: Installation &amp; Upgrades
---

### Post by gwilson on 2006-03-14
Hi,

Just some opinions and observations that may be useful to newcomers.

I've played with Ubuntu now since Hoary and have just switched over from Breezy to Dapper with few issues. I'd recommend that newcomers stick to Breezy until the final Dapper is released since there is some tweaking to do.

I prefer the look and feel of Gnome to that of the KDE desktop. KDE is just a bit too glitzy, and you just can't get rid of some of the geegaws I don't like. Gnome may be less intuitive in the configuration area, but you get to know it and can get it to do what you want it to. XFCE is also a nice desktop manager, but Gnome is a little bit more mainstream.  I primarily use any desktop to organize my computer and as a program launcher.

Most KDE programs run perfectly under Gnome with only a portion of the full KDE package installed. Synaptic Package Manager will install the needed files automatically. Amarok, Gwenview, K3B are excellent KDE apps that I wouldn't do without even though I'm a Gnome guy. Krusader file manager is also great. Kontact almost beats out Evolution, but the included Kmail lacks a couple of features I require.

I'm not that good at installing software that is not in the Ubuntu repositories, although I have managed to do so just to get the bleeding edge version of something. It's a major pain that all of the proprietary (licensed,non-free) multimedia plug-ins and W32 codecs are not included in Ubuntu, but the ethics of that are right. I use Automatix to install these and some other bits in Breezy. Sometimes these third-party privat scripts can mess things up a bit, but they are generally bug-free at this point and do so much for you. Automatix does not work for Dapper, but there are similar scripts in the forums that can take care of this for you.

I have a separate 20 Gig partition where I install various Linux distributions and play with them. I also have Windows ME and XP on my computer. Grub manages all the booting. Ubuntu can read and write FAT partitions like those of Windows ME, but can only read the NTFS partitions that XP uses. (I suspect that Linux can be made to write to an NTFS partition, as well, but you would mess it up royally.) I maintain a 20 Gig FAT32 partition that can be read and written to by both Windows and Ubuntu. I keep all of my stored music files and images there where they can be accessed from either Linux or XP without having to duplicate the files.

I did a clean install of Dapper Flight 5 to my experimental 20 Gig partition, and it runs well. After installing all of the programs I use frequently and copying over some data files from the Breezy partition, I was shocked to see that my Dapper system only occupied less than 4 Gigs whereas my Breezy system is at around 12 Gigs with mostly the same software (definitely fewer window managers, though). I think when you install and uninstall many programs over a period of time that a lot of DEB files and other things stay on your computer even if you uninstall a package using the "complete removal" option.

When you do a new clean install of Dapper to a separate partition, it turns out to be relatively simple to copy all of your mail, address, and bookmarks to the new system. Just about everything can be found in your Home directory and copied. 

I'm not offering details here, but there are lots of instructions in previous forum messages if you search for them.

Things you ought to make an effort to learn include the following:

Learn how to install and configure GRUB. It isn't that hard and can make things much easier if you have several operating systems on your computer. Grub can handle Windows XP booting just fine; XP can't deal well with any other systems.

Learn how to launch applications with root priveleges so that you can change file permissions and write to certain protected configuration files when necessary. Obviously, you need to know how to properly alter these files or you'll mess things up. Frequently, you can launch file browsers and text editing programs with root privileges by adding new menu entries with a few letters added to the command execution.

Learn to use the menu editor. 

Become familiar with half a dozen important configuration files and how they work. These include things like /etc/fstab and /etc/mtab (how drives and partions are handled), /etc/X11/xorg.conf (or the equivalent for your video system or display), grub files, sudoers file. They have great power for Good and Niceness, but also great potential to mess up your system.

If you do mess things up, there are a few command line programs you can run when the command line is all you have that can help you go in and fix things. Just knowing a little about these can salvage an entire system with a few keystrokes.

Above all, DON'T PANIC!  If something stops working, you can usually fix it without formating your drives and reinstalling everything. Keep a cool head and use a little knowledge. One great advantage of having more that one operating system (even two Linux systems) on one computer is that you can still get access to the web to get advice and information from the forums.

Again, these are just general observations, but you should be aware that there are all kinds of tips and tricks in the forums and that a little bit of knowledge can get you out of trouble as well as get you into it!

;-)

GW

---

### Post by Joe Driller on 2006-03-14
Thanks for information. I am new to Linux World, I started using Ubuntu 5.10 with Gnome in a Dual PIII 500 Mhz Box with 256 RAM and I noticed that was a bit slow, a friend of mine tell me to use Kubuntu because he uses it and he can help me with my doubts. I've changed to Kubuntu and for my surprise I feel that KDE is faster than Gnome but I heard time ago that ususally Gnome is fater than KDE.
Is this true?


Thanks in advance.

José Coma

---

### Post by Adrian on 2006-03-14
[QUOTE=Joe Driller]I've changed to Kubuntu and for my surprise I feel that KDE is faster than Gnome but I heard time ago that ususally Gnome is fater than KDE.[/QUOTE]

On my 700MHz laptop, KDE is definitely faster.

---

### Post by tmahmood on 2006-03-14
I use GNOME but yea sometimes I feel KDE is lot faster then GNOME. but the GNOME I'm using in Dapper Flight 4 is really fast :) and GNOME 14 is going to be faster.

---

### Post by louca on 2006-04-24
is it possible to copy any files from the windows ntfs partition/hd to the ubuntu partition/hd though?

also, how do you allow user access to the windows partition? :?

---

### Post by Jagot on 2006-04-25
[QUOTE=louca]is it possible to copy any files from the windows ntfs partition/hd to the ubuntu partition/hd though?

also, how do you allow user access to the windows partition? :?[/QUOTE]


[http://help.ubuntu.com/starterguide/C/ch05.html](http://help.ubuntu.com/starterguide/C/ch05.html)

---

