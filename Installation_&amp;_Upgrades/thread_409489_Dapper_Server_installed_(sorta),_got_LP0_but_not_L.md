---
title: "Dapper Server installed (sorta), got LP0 but not LP1"
date: 2007-04-14
forum: Installation &amp; Upgrades
---

### Post by MPH on 2007-04-14
**Background:**
This is my first Linux post.  I’m a Linux Noobie but an old hand with command line interpreters (CLIs), programming and building PCs.  After buying a laptop mostly for my wife, I networked it with my desktop and our Internet connection.  With a 1995-vintage Gateway PC gathering dust, I bought a KVM switch and network card with the goal of learning something about Linux in the process of building a Samba server for our home.  Ideally, I’d love to recycle many vintage PCs into file and print servers for the growing number of networked households… and maybe small businesses.  What better way to give people a good impression of Ubuntu???

**Installing the server had a few hitches:**
I burnt a CD-R from the Dapper Server iso but the PC wouldn’t boot the iso CD… nor a 2003 Norton Systemworks CD.  After googling the problem, I guessed the old PC’s BIOS couldn’t boot a CD in “no emulation mode” but it eventually booted the CD via a MS-DOS floppy, GRUB4DOS and a MENU.LST file that INSTLUX “provides”.  The problem with booting that way was that it didn’t invoke the expected start-up screen with the server installation options.  Instead, it just went ahead and installed whatever it wished.  Apparently, it wasn’t a LAMP server which suits my old PC best but I have no idea if the process skipped any important steps.  Since APTITUDE has been able to install SAMBA and perform several updates, I assume the system is generally intact.

**Expectations:**
As a Linux noobie who has read the Ubuntu Server Guide, The Ubuntu Server chapter of The Offical Ubuntu Book and gone nearly blind reading “too much” Ubuntu and Googled Linux documentation, I humbly come here for guidance.

I was originally happy that the server came with no GUI, especially with the PC having only a 200MHz CPU and 80MB of RAM.  Unfortuantely, the documentation I’ve encountered is weakest in describing how Ubuntu, Debian, or Linux reveals the details of installed hardware and resolving hardware issues via the CLI.

The Gateway PC has an adapter card with a parallel port and a serial port on it so I expected the SAMBA server to eventually be able to serve my laser printer and Deskjet printer from the PC’s two parallel ports.  However, “sudo ls /dev/lp*” lists only “lp0” so apparently only one printer port is installed.  Isn’t it most likely that the parallel port on the adapter card didn’t install?

**At this point, I’m still in the dark about how to…**

·	check out by CLI what hardware Ubuntu considers installed and fully operational.
·	install or reinstall hardware by CLI.  Just how automatic is the process?  Can I force a piece of hardware to be reinstalled by removing the installed device driver?
·	find relatively comprehensive CLI documentation for administering server hardware and diagnosing hardware problems.
·	determine if it would be wise to install a simple GUI.  I read that “Fluxbox is a lightweight and responsive window manager for GNU/Linux.”  I presume that means it is only a GUI server.  I don’t have a Linux desktop to use as a GUI client.  I presume that there well could be a free Windows client for the X-Window system that would interface with Fluxbox or whatever to manage a Ubuntu server running on functionally lightweight hardware.  Please advise me about the practicality of this option… or kindly offer a better GUI solution as long as it doesn’t involve installing the Ubuntu desktop on one of my Windows PCs.  (I’m not ready to install and dual boot or VM the Ubuntu desktop on a Windows PC… at least not until this project is successful.)

Thanks so much for reading this far… my goal was to say enough to minimize the number of questions readers would have to ask.  BTW… I think Ubuntu server was a great choice!  I expected more problems than this!!!

---

