---
title: "Need help w/ VMware Venturecake.com guide"
date: 2007-07-12
forum: Installation &amp; Upgrades
---

### Post by kris2pe on 2007-07-12
Reference
[http://www.venturecake.com/10-minutes-to-run-every-windows-app-seamlessly-on-your-ubuntu-desktop/#more-10](http://www.venturecake.com/10-minutes-to-run-every-windows-app-seamlessly-on-your-ubuntu-desktop/#more-10)
Here is the guide
    * Click Applications &#8594; Add/Remove&#8230; install the vmware-server package.
    * Click System &#8594; Administration &#8594; Synaptic Package Manager. Install the rdesktop package.
[COLOR="Olive"]Its already installed so I didn't install it anymore![/COLOR]
    * Click Applications &#8594; System Tools &#8594; VMware Server Console
      When VMware Server Console starts, click Connect to attach to your local machine. Then Create a New Virtual Machine. Use all the defaults, but pick NAT networking. Pop in your Windows CD, and install Windows
    * Once Windows has started:
          o Enable Terminal Services by clicking Start &#8594; Control Panel &#8594; System. Click the Remote tab, and enable Allow users to connect remotely to this computer
[COLOR="Olive"]I'm not sure If this was disabled in services.msc. But I think was able to connect to the net. [/COLOR]
          o Turn off the desktop for the user you&#8217;ll use to run your Windows apps, by clicking Start &#8594; Run typing regedit and selecting HKEY_CURRENT_USER/Software/Microsoft/Windows/ CurrentVersion/Policies/Explorer. Create a DWORD called NoDesktop set to 1.
[COLOR="Olive"]On regedit Dword is NoDesktop hex=1[/COLOR]
          o Note the IP address of Windows. Clicking Start &#8594; Connect to &#8594; Show All Connections. Select the Local Area Connection and hit the Support tab
[COLOR="Olive"]Copied already[/COLOR]
          o Download SeamlessRDP, then extract it to C:\seamlessrdp
[COLOR="Olive"]Downloaded & put in the exact directory[/COLOR]
          o Log out of Windows, and close VMware Server Console (leave the VM running)
[COLOR="Olive"]Kinda confuse w/ this! But what I did was close the vm tab of xp prof[/COLOR]
    * Back in Ubuntu, open a Terminal, and run:
          rdesktop -A -s &#8216;c:\seamlessrdp\seamlessrdpshell.exe c:\windows\explorer.exe&#8217; IPAddress -u user -p password

[COLOR="Olive"]I didn't not change the the user & password! 
I didn't see xp integrated in my ubuntu[/COLOR]

      substituting the IP address you noted earlier. 
[COLOR="Olive"]Yup I did substitute it w/ the copied ip no. is xp! [/COLOR]


_________________________________________________________________________________________________________
The result are these lines of code nothing more & nothing less

Usage: rdesktop [options] server[:port]
   -u: user name
   -d: domain
   -s: shell
   -c: working directory
   -p: password (- to prompt)
   -n: client hostname
   -k: keyboard layout on server (en-us, de, sv, etc.)
   -g: desktop geometry (WxH)
   -f: full-screen mode
   -b: force bitmap updates
   -L: local codepage
   -A: enable SeamlessRDP mode
   -B: use BackingStore of X-server (if available)
   -e: disable encryption (French TS)
   -E: disable encryption from client to server
   -m: do not send motion events
   -C: use private colour map
   -D: hide window manager decorations
   -K: keep window manager key bindings
   -S: caption button size (single application mode)
   -T: window title
   -N: enable numlock syncronization
   -X: embed into another window with a given id.
   -a: connection colour depth
   -z: enable rdp compression
   -x: RDP5 experience (m[odem 28.8], b[roadband], l[an] or hex nr.)
   -P: use persistent bitmap caching
   -r: enable specified device redirection (this flag can be repeated)
         '-r comport:COM1=/dev/ttyS0': enable serial redirection of /dev/ttyS0 to COM1
             or      COM1=/dev/ttyS0,COM2=/dev/ttyS1
         '-r disk:floppy=/mnt/floppy': enable redirection of /mnt/floppy to 'floppy' share
             or   'floppy=/mnt/floppy,cdrom=/mnt/cdrom'
         '-r clientname=<client name>': Set the client name displayed
             for redirected disks
         '-r lptport:LPT1=/dev/lp0': enable parallel redirection of /dev/lp0 to LPT1
             or      LPT1=/dev/lp0,LPT2=/dev/lp1
         '-r printer:mydeskjet': enable printer redirection
             or      mydeskjet="HP LaserJet IIIP" to enter server driver as well
         '-r sound:[local|off|remote]': enable sound redirection
                     remote would leave sound on server
         '-r clipboard:[off|PRIMARYCLIPBOARD|CLIPBOARD]': enable clipboard
                      redirection.
                      'PRIMARYCLIPBOARD' looks at both PRIMARY and CLIPBOARD
                      when sending data to server.
                      'CLIPBOARD' looks at only CLIPBOARD.
   -0: attach to console
   -4: use RDP version 4
   -5: use RDP version 5 (default)

---

### Post by tolremeno on 2007-07-13
Most of your questions are answered in the comments at venturecake, I think, although I can't get it quite right, either.

---

