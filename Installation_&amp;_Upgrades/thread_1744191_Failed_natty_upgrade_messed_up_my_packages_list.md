---
title: "Failed natty upgrade messed up my packages list"
date: 2011-04-30
forum: Installation &amp; Upgrades
---

### Post by adampatch on 2011-04-30
I was mid-upgrade from meercat to natty when my web connection failed. The update manager was in the process of updating the sources lists. I restarted update manager and got this error:


Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/fr.archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'


I get the same error on running software center and when i try using apt-get directly i get 

E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/fr.archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

I tried copying status-old to status in /var/lib/dpkg but that changed nothing.

And that's as far as i've got. It seems fairly clear to me what the problem is but i'm far too much of a casual user to be able to fix it. Presumably i need to sort out my software sources list but i've only ever edited this through the software-center and since this crashes on startup (with the above error message) i'm now stuck.

Any help would be much appreciated

---

### Post by dino99 on 2011-04-30
if you can boot in recovery mode ("shift" key down at bios end process to get grub menu) then select "repair packages"

note: the servers are very (too) busy due to the huge requests for upgrading/installing natty and often send errors. It should be easier in a few days and will get some fixes too

---

### Post by adampatch on 2011-04-30
Thanks for the reply. I just tried it but no luck. Trouble is i can't access the web in recovery mode (i'm using a wireless connection that i have to log into). I get a long list of 'failed to resolve' messages for various sources and then the same error message as posted previously. I guess i'll have to wait till after the weekend when i'll be seeing a mate whose fixed internet connection i can use. Then i can either use your fix or just download the full iso. Thanks again

---

