---
title: "Black Screen after Update - Ubuntu 14.04 in VMWare"
date: 2015-01-19
forum: Installation &amp; Upgrades
---

### Post by chris_h2 on 2015-01-19
I have been using Ubuntu in a VM for months without any issues, and when I first booted up today it told me there were updates and went ahead. I didn't reboot straight after the updates, I carried on with what I was doing.
 I decided I was going to take a snapshot because I've made some progress, but decided to do it after rebooting to take the update into account.
 After rebooting I get:
 1. A very brief purple screen,
 2. An underline, at which I can type stuff but doesn't appear to do anything
 3. A purple screen with the dots being filled in
 4. The black screen.
I now can't do anything.
The web site I'm developing appears to be working and my SMB shares are working.
 Unfortunately I hadn't set up remote telnet access, so using Putty with or without SSH doesn't seem to work. Standard tenet session just disappears and SSH gives me "Network Error: connection refused"
 Hitting some random keys whilst booting sometimes takes me into a recovery menu, where I can select various options. Dropping to root doesn't let me do anything - it says it's in read-only mode. clean, dpkg and fsck seem to stick doing nothing after telling me how many files and blocks there are. The failsafe graphics boots back to the black screen. I tried all the previous versions and their failsafe (ha!) modes. I don't know what to try next.
I have tried defragging the disk and allocating more disk space and more RAM - no different.
 Any advice appreciated.
 Thanks,
 Chris

---

### Post by chris_h2 on 2015-01-20
Just to check, I have created a newly installed VM using Ubuntu 14.04.1 and ran all the updates and it boots ok.
The original VM I talked about before still boots to a black screen.
If I could reach my home directory I could copy all my stuff over to the new VM, although it would take a few hours to reinstall and reconfigure all the packages and permissions I'd set up.
It's very weird how it seems to all start up properly except for the display, which shows there are no problems in booting up, just in displaying the desktop. The purple splash screen displays fine.
If I could start a command prompt I could see if reinstalling VMware tools would sort out the issue.

---

### Post by heatherlee on 2015-03-25
[SIZE=2][FONT=arial]In order to access a console:[/FONT][/SIZE]
[LIST]
[*][SIZE=2][FONT=arial] immediately after starting the VM, click into the VM window and press and hold the shift button while the system boots.[/FONT][/SIZE]
[*][SIZE=2][FONT=arial]select a recovery instance of Ubuntu from the menu of boot options.[/FONT][/SIZE]
[*][SIZE=2][FONT=arial]when a list of options for recovery modes is listed, select enable networking.[/FONT][/SIZE]
[*][SIZE=2][FONT=arial]when the list returns (after enabling networking) select to login as root.[/FONT][/SIZE]
[/LIST]
[SIZE=2][FONT=arial]You've now got a networked root console and can grab your stuff however you please.  However, when faced with the same problem, I was able to save my whole instance.  The VMware tools software installed on the guest machine was making Ubuntu's X unhappy.[/FONT][/SIZE]
[LIST]
[*][SIZE=2][FONT=arial]from console in VM, navigate to where you unpacked the VMware tools package.[/FONT][/SIZE]
[*][SIZE=2][FONT=courier new]#vmware-uninstall-tools.pl[/FONT][/SIZE]
[*][SIZE=2][FONT=courier new]#reboot[/FONT][FONT=courier new][/FONT][/SIZE]
[/LIST]
[FONT=arial]&#8203;If you're brave, then after upgrading Fusion (Menu Bar -> VMWare Fusion -> Check for updates...) and Ubuntu ([/FONT][FONT=courier new]$sudo apt-get upgrade[/FONT][FONT=arial]) you could try reinstalling the VMware tools.  Or just live without inter-system cut-and-paste and whatever else VMware tools does.[/FONT]

---

