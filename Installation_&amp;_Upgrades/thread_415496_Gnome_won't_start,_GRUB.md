---
title: "Gnome won't start, GRUB"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by uniontroublemaker on 2007-04-20
1) I upgraded from edgy to feisty.  Everthing went fine, but gnome will not start.  It is a problem with the nvidia driver.  I have GeForce 420.  This happened when I upgraded from Dapper.  I just cannot find/remember the solution.  I used Automatix to install the driver.
2) Windows is not in GRUB.  Normally I correct this with gksudo gedit but cannot do this without Gnome.  Is there a way to edit GRUB from command-line?

---

### Post by pepsi_max2k on 2007-04-20
for 1 i've no idea.

for 2, yeah you can use vi on a command line to edit the file. log in as root and "vi /boot/grub/menu.lst". a list of vi commands is here: [http://www.cs.colostate.edu/helpdocs/vi.html](http://www.cs.colostate.edu/helpdocs/vi.html)  but basically it's just up/down to select a line to edit, "dd" deletes the whole line, "i" lets you edit the text (delete to delete characters, type stuff to add more) then hit Esc to exit out, and then type ":wq" to write and quit or ":q!" to just quit with no write.

---

### Post by lugburz on 2007-04-20
have you try with:

$ sudo emacs

---

### Post by uniontroublemaker on 2007-04-22
Thanks for your help. 

With help from other posts, I got Gnome up and running.  

Apparently, my Nvidia GeForce4 MX 420 graphics cards is no longer directly supported.

For anyone with the same problem, I entered from the command-line:

sudo dpkg-reconfigure xserver-xorg

Then I entered all the defaults and instead of Nvidia, chose vesa .

Then I re-booted.  Gnome loaded up this time.

To install the Nvidia driver from within Gnome, I downloaded and installed Envy from
[http://albertomilone.com](http://albertomilone.com)
It downloads the new driver and configures it automatically.

---

