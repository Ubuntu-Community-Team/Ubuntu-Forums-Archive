---
title: "VMware {Player Ubuntu 9.10 Mouse Integration"
date: 2009-10-12
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by tkornacki on 2009-10-12
Just wondering if anyone is running VMware Player with a ubuntu 9.10 host and Windows XP machine with VMware tools installed successfully?

I just upgraded to ubuntu 9.10 and have found that the mouse integration is not working properly.  It seems to jump in and out towards the edges of the window therefore preventing things from being clicked  e.g.  windows start button as the first click grabs the VM window (then it falls out).  So the second mouse click simply grabs the window again.

This problem is in console mode.  When in unity mode it seems to work ok.

I am using:

VMware Player 2.5.3 build-185404
ubuntu release 9.10 (karmic) (64bit)
kernel linux 2.6.31-13-generic
GNOME 2.28.0

Does anyone have any ideas of how to get around this or at least identify if its ubuntu or VMware that has the issue?

Cheers.

---

### Post by Gazi on 2009-10-14
I have the same problem with same versions.

---

### Post by gungne on 2009-10-19
I had the same problem and found this solution which worked for me:
[http://www.rootloot.de/blog/vmware_in_ubuntu_karmic](http://www.rootloot.de/blog/vmware_in_ubuntu_karmic)

Pu[FONT=Arial]t this statement

[/FONT]export VMWARE_USE_SHIPPED_GTK=yes

[FONT=Arial]into [/FONT]/etc/vmware/bootstrap

Cheers,
Arne Hanssen

---

### Post by dabl on 2009-10-19
... and be aware that VMware won't build correctly on the next kernel you install.  You will need to first comment out that line in /etc/vmware/bootstrap, then run VMware and let it build the modules and open your VM, then close it all, and go back into /etc/vmware/bootstrap and uncomment the line.  Then it will run correctly once again.

---

### Post by ayates on 2009-10-19
There's also a beta verion of Player(VMware-Player-3.0.0-197124.i386.bundle) that fixes it.

---

### Post by sdowney717 on 2009-10-26
nasty problem but easy to work around
this fixes the problem for me vmware server 2.0.1 
mouse is now working!

create this file using the bin/bash text.
give it a name like VMlaunch.sh
make it executable
run it and it loads the VMware machine
> #!/bin/bash
################################################################################
# Call VMWare Server's Remote Console in a clean GTK setup.
################################################################################

# Clean GTK setup for VMWare
export VMWARE_USE_SHIPPED_GTK=yes

# Find console executable in Firefox plugins.
vmrc="$(find "$HOME/.mozilla/firefox" -name vmware-vmrc -type f -perm -111 | tail -1)"
[ -x "$vmrc" ] || exit 1

set -x
cd "$(dirname "$vmrc")" && "$vmrc" -h 127.0.0.1:8333





[http://shellack.de/info/content/vmware-server-20-console-failure](http://shellack.de/info/content/vmware-server-20-console-failure)
It should also be possible to run Firefox by VMWARE_USE_SHIPPED_GTK=yes firefox in your Linux command line to fix the GTK issue.
sdowney717 wrote 2 seconds ago: 	#6

---

### Post by sdowney717 on 2009-10-26
interesting, if you run the script and the virtual machine is powered off, it will power it on. so once you have the machine configured, the script simply acts as a player.

how about the sound, it says it is not compatable.

---

### Post by ivano.visco on 2009-10-27
> **gungne said:**
> I had the same problem and found this solution which worked for me:
[http://www.rootloot.de/blog/vmware_in_ubuntu_karmic](http://www.rootloot.de/blog/vmware_in_ubuntu_karmic)

Pu[FONT=Arial]t this statement

[/FONT]export VMWARE_USE_SHIPPED_GTK=yes

[FONT=Arial]into [/FONT]/etc/vmware/bootstrap

Cheers,
Arne Hanssen

This worked for me too. :D Thanks

---

### Post by bribera on 2009-10-27
> **gungne said:**
> I had the same problem and found this export VMWARE_USE_SHIPPED_GTK=yes


Interestingly enough, this fix fails rather unimpressively under xubuntu/x86_64/vmware-server 2.0.1:

[INDENT][FONT="Courier New"]brendan@scylla:[snip]$ VMWARE_USE_SHIPPED_GTK=yes ./vmware-vmrc -h 127.0.0.1:8333

(vmware-vmrc:19752): Gtk-WARNING **: GModule initialization check failed: Gtk+ version too old (micro mismatch)

(vmware-vmrc:19752): Gtk-WARNING **: GModule initialization check failed: Gtk+ version too old (micro mismatch)
** (vmware-vmrc:19752): DEBUG: This Gtk+ version doesn't have the GtkSettings::gtk-enable-input-feedback-sounds property.
./bin/vmware-vmrc: symbol lookup error: /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: undefined symbol: gdk_threads_add_idle_full[/FONT][/INDENT]

I don't quite grok the different values for this variable, but setting it to "**force**" instead of "yes" in my setup caused things to function correctly.

I.e. try:

[INDENT][FONT="Courier New"]VMWARE_USE_SHIPPED_GTK=force
[/FONT][/INDENT]
If you're still having issues.

---

