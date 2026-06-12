---
title: "Lucid Beta 1 -  X fails to load properly"
date: 2010-04-01
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by zakmakattak on 2010-04-01
Hi all,

My problem is this:
I recently upgraded from karmic to lucid beta 1, and when I attempt to boot, X, doesn't initialize properly.  I see my wallpaper, and a cursor, but nothing else loads.  No icons, no toolbar, nothing.

I ran recovery mode and tried startx to see if it was generating any error messages, and I got:

"[dix] couldn't enable device 12"

I'm on an HP notebook, model dv1315cl.
My video card is a Intel 915GM Chipset.
Processor is Intel Centrino.

Tried googling this, but came up with nil.  Anyone have any suggestions?

---

### Post by garvinrick4 on 2010-04-01
So it is your gnome-panel that is not loading.
If you have a short cut to your terminal and can get to it.
code: aptitude show gnome-panel

See if it is loaded. 

I have been thru this and just cannot remember what I did, I am sure I found it
by Googling it. Will keep thinking and if it hits me will post. It was a simple procedure
though that I remember.

---

### Post by zakmakattak on 2010-04-01
gnome-panel is loaded, so I guess that's not it. =(

---

### Post by garvinrick4 on 2010-04-01
> **zakmakattak said:**
> gnome-panel is loaded, so I guess that's not it. =(
It may be there but it is not loading!!

---

### Post by zakmakattak on 2010-04-01
Ok, I checked via "top" and gnome-panel is indeed NOT running.  Any idea how to go about fixing this?

---

### Post by garvinrick4 on 2010-04-02
> **zakmakattak said:**
> Ok, I checked via "top" and gnome-panel is indeed NOT running.  Any idea how to go about fixing this?
First, I created a launcher for Terminal. Right Click on any area on  the desktop and then choose ‘Create Launcher’. Choose any name and then  in the command text box, type in
  terminal

  This should create a terminal launcher. That done, double click to  open a terminal session. Enter the following command,
  [COLOR=#C20CB9]**killall**[/COLOR] gnome-panel

  Then right click on the desktop to create another launcher. This time  in the command text box, type in
  gnome-panel

  This creates a gnome-panel launcher. Double click and you have panels.


If you have a terminal just do second and third step.

---

### Post by zakmakattak on 2010-04-02
I can't open a terminal, right-clicking on my desktop background is unresponsive.

I tried doing it through the command-line, but when I try to initialize gnome-panel, it gives me "Gtk WARNING **: cannot open display:"

---

### Post by garvinrick4 on 2010-04-02
I wonder if your whole gdm is stricken.


Put in your install CD or live CD same thing.
Open gparted and see what your lucid install is sda1, sda2, sda5 so on.
right click on it and Label it lucid and then apply it.

Now lets say it is sda5 and you did label it lucid. Replace sda5 with whatever yours is.

sudo mkdir /media/lucid (space after mkdir)makes a directory or folder.

sudo mount /dev/sda5 /media/lucid (mounts your lucid partition)

sudo cp /etc/resolv.conf /media/lucid/etc/relsolv.conf     (gets internet connection)

sudo chroot /media/lucid (now you are in root for lucid)

apt-get install -f  (fix broken packages)

apt-get clean   (clean your cache)

now remove then reinstall packages that could be bad. (gnome-panel) (gdm)

apt-get update && apt-get upgrade

Hit ctrl and D

sudo umount /media/lucid    (unmount lucid that is not a typo umount)


Must have right spacing in code:

shutdown; take out cd and restart:

---

### Post by zakmakattak on 2010-04-02
I did everything posted above, but alas, the problem persists :(

---

### Post by garvinrick4 on 2010-04-02
try removing a program called plymouth it is the splash screen that beta is 
having trouble with. I have to remove it to boot and a lot of others also.

sudo apt-get remove plymouth


They say it will be fine by beta2

---

### Post by zakmakattak on 2010-04-02
I attempted to uninstall plymouth, but when I did so, apt-get told me I needed to additionally uninstall >2GB worth of system files, including my kernel.

I've reverted back to karmic, and I think I'm going to stay here at least until Beta 2 comes out.  Thank you for all your help though.

---

