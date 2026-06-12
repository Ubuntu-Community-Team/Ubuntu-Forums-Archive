---
title: "vmware server 2.0 in intrepid ibex"
date: 2008-09-30
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by SpUpUz on 2008-09-30
vmware server 2.0 console keaybord not working!!

all works cool except the keybords on virtual machine console, for example direction key are not mapped correctly.

---

### Post by Delvien on 2008-09-30
> **SpUpUz said:**
> vmware server 2.0 console keaybord not working!!

all works cool except the keybords on virtual machine console, for example direction key are not mapped correctly.

Couldn't get mine to configure.

---

### Post by SpUpUz on 2008-09-30
> **Delvien said:**
> Couldn't get mine to configure.

what do you mean?

---

### Post by Delvien on 2008-10-01
> **SpUpUz said:**
> what do you mean?

Theres... no other way to say it... vmware wont configure for me

---

### Post by SpUpUz on 2008-10-01
> **Delvien said:**
> Theres... no other way to say it... vmware wont configure for me

for me eveything seems ok but going in console for the up arrow key it corresponds the "*" and also for down arrow, so i can't use ctrl alt del and cant select a diffrent hardware profile in my windows box

---

### Post by SpUpUz on 2008-10-03
any other one as tested this environment

---

### Post by SpUpUz on 2008-10-03
ok tested the same environment at home and as a result i have got the same issue arrow key are not usable!! and can't login correclty!

---

### Post by jms-ubuntu-en on 2008-10-05
My problem is that I can't log in to virtual machine (xp) because I can't enter ctrl-alt-del. Ctrl-alt is reserved for remote console's "Release Input" :confused:
Any suggestions?

---

### Post by dabl on 2008-10-05
I'm not sure about VMware server, but there's a new VMware Player, ver. 2.5, which installs on the 2.6.27-5 kernel with no problem. 2.0.5 won't configure on kernels after 2.5.26, AFAIK.

[http://www.vmware.com/download/player/](http://www.vmware.com/download/player/)

However, after setting up my Win XP VM, it also exhibits a keyboard problem -- the arrow keys don't function.  All other keys appear to work correctly.  The same VM works perfectly on 2.0.5, which is running on a 2.6.25 kernel.  The keyboard and driver is the same in Windows device manager.  The mouse works correctly.

---

### Post by jms-ubuntu-en on 2008-10-06
I just remembered that I had enabled RDP in my virtual XP. So I created new port forwarding rule to /etc/vmware/vmnet8/nat/nat.conf

# RDP
2289 = 192.168.65.128:3389

After restarting vmware service it was possible to use tsclient to connect localhost:2289

---

### Post by tact on 2008-10-06
Vmware Server 2 compiles and runs fine for me in intrepid.  (See below for the output at the end of the compile/configure).

I wonder - if your up arrow yields a "*" character - could the VM keymap and "num lock" be implicated?  It may be nothing but coincidence but on my laptop if I use the main keyboard as a numeric keyboard (i.e. numlock on)  the "*" key can also be "up".

As for passing a "crtl-alt-del" to windows -  good question...  I wonder why it seems left out from VMware server 2.  It was there in 1.x.x via a menu

======
Starting VMware services:
   Virtual machine monitor                                             done
   Virtual machine communication interface                             done
   Virtual ethernet                                                    done
   Bridged networking on /dev/vmnet0                                   done
   Bridged networking on /dev/vmnet2                                   done
   Host-only networking on /dev/vmnet8 (background)                    done
   DHCP server on /dev/vmnet8                                          done
   NAT service on /dev/vmnet8                                          done
   VMware Server Authentication Daemon (background)                    done
   Shared Memory Available                                             done
Starting VMware management services:
   VMware Server Host Agent (background)                               done
   VMware Virtual Infrastructure Web Access
Starting VMware autostart virtual machines:
   Virtual machines                                                    done

The configuration of VMware Server 2.0.0 build-116503 for Linux for this 
running kernel completed successfully.

$ uname -r
2.6.27-5-generic
==============

---

### Post by SpUpUz on 2008-10-06
> **tact said:**
> Vmware Server 2 compiles and runs fine for me in intrepid.  (See below for the output at the end of the compile/configure).

I wonder - if your up arrow yields a "*" character - could the VM keymap and "num lock" be implicated?  It may be nothing but coincidence but on my laptop if I use the main keyboard as a numeric keyboard (i.e. numlock on)  the "*" key can also be "up".

As for passing a "crtl-alt-del" to windows -  good question...  I wonder why it seems left out from VMware server 2.  It was there in 1.x.x via a menu

======
Starting VMware services:
   Virtual machine monitor                                             done
   Virtual machine communication interface                             done
   Virtual ethernet                                                    done
   Bridged networking on /dev/vmnet0                                   done
   Bridged networking on /dev/vmnet2                                   done
   Host-only networking on /dev/vmnet8 (background)                    done
   DHCP server on /dev/vmnet8                                          done
   NAT service on /dev/vmnet8                                          done
   VMware Server Authentication Daemon (background)                    done
   Shared Memory Available                                             done
Starting VMware management services:
   VMware Server Host Agent (background)                               done
   VMware Virtual Infrastructure Web Access
Starting VMware autostart virtual machines:
   Virtual machines                                                    done

The configuration of VMware Server 2.0.0 build-116503 for Linux for this 
running kernel completed successfully.

$ uname -r
2.6.27-5-generic
==============

i have got the same situation :lolflag:

---

### Post by tom17 on 2008-10-06
Similar prob here.

Intrepid 64 bit host. VMWare Server 2. VMWare Viewer in firefox. Windows XP Guest.

Up arrow key seems to do nothing, left arrow maps to alt. Left alt is also alt, but right alt seems to map to the enter key. Down brings up the start menu. Right arrow does nothing.

very strange 

Help!

Tom...

edit: Well whaddaya know.. this fixed it... [http://nthrbldyblg.blogspot.com/2008/06/vmware-and-fubar-keyboard-effect.html]("http://nthrbldyblg.blogspot.com/2008/06/vmware-and-fubar-keyboard-effect.html")

---

### Post by geofb on 2008-10-07
Using the NumPad on Logitech Access keyboard works for me.
Ctrl-Alt-(numpad)Del to login to Windows guest via VMWare console.
Then the arrow keys on the NumPad to move around in the Windows guest.

---

### Post by SpUpUz on 2008-10-07
> **tom17 said:**
> Similar prob here.

Intrepid 64 bit host. VMWare Server 2. VMWare Viewer in firefox. Windows XP Guest.

Up arrow key seems to do nothing, left arrow maps to alt. Left alt is also alt, but right alt seems to map to the enter key. Down brings up the start menu. Right arrow does nothing.

very strange 

Help!

Tom...

edit: Well whaddaya know.. this fixed it... [http://nthrbldyblg.blogspot.com/2008/06/vmware-and-fubar-keyboard-effect.html]("http://nthrbldyblg.blogspot.com/2008/06/vmware-and-fubar-keyboard-effect.html")

going to try that.

---

### Post by tombott on 2008-10-29
the Ctrl-Alt and Num Pad Del works a treat.
I just find it really odd they left a Send Ctrl-Alt-Del command out of this version.

---

