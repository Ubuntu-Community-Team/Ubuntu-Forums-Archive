---
title: "my package manager/updater has crashed"
date: 2013-06-29
forum: Installation &amp; Upgrades
---

### Post by woodsyboredom on 2013-06-29
My soft ware ceneter and updater has crashed and will not run. I would like to try booting up in recovery mode but I cannpt figure how to do this in unbuntu 13.04. any help would be greatly appreciated. Also the crash reporting program seems to be affected so that the crash reportrs that are generated, if they even are. don't seem to be sent.

---

### Post by Bashing-om on 2013-06-29
woodsyboredom; Hi !

Can you boot to your desktop ? If so we can run some terminal commands and determine the state of the package manager and then look at the GUI update problems from a lower perspective.

[INDENT][INDENT]try'n to help[/INDENT][/INDENT]

---

### Post by woodsyboredom on 2013-06-30
i can boot on my desktop and it runs fine. the problrm is with my laptop. the package manager is messed up. I get this error message: *An error occurred, please run Package Manager from the right-click menu or apt-get in a terminal to see what is wrong.The error message was: 'Error: Opening the cache (E:Encoontered a section with no Package header, E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_raring-updates_main_i18n_Translation-en, E: The package or status file could not be parsed or opened.)'. This usually means that your installed packageshave unmet dependencies. * my main problem is with being able to open or run the software updater or synaptic package manager I don't know how to find what is missing. also my grub skills in terminal are really limited.

---

### Post by woodsyboredom on 2013-06-30
I get this when i open synaptic package manager: 
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_raring-updates_main_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

---

### Post by woodsyboredom on 2013-06-30
should I run the Remove orphaned packages App?

---

### Post by Bashing-om on 2013-06-30
woodsyboredom; Hi ! Good morning .

Let's clean things up a bit, remove that damaged package list ... and repopulate it; Thus: -> Terminal codes:
```

sudo apt-get clean
sudo rm -fr /var/lib/apt/lists
sudo mkdir -pv /var/lib/apt/lists/partial
sudo apt-get update ##will bring in new scripts that should not be broken.

```

Which I anticipate will fix ya up finer than an Ozark fiddle.

[INDENT][INDENT]where there is a will there is a way[/INDENT][/INDENT]

---

### Post by woodsyboredom on 2013-06-30
OMG! that fixed it lickety split!!!! thank you thank you thank you! this is anther reason why ubuntu is so great people like you out there willing and able to help thanks soooooo much

---

### Post by Bashing-om on 2013-06-30
woodsyboredom; Hey great !

Glad it is resolved... look'n good.
Remember, this is open source, one for all and all for one ... we are in this together. Just pass the assit on down the line.

Please mark this thread as solved; Aides others seeking a solution, as well as; Helps keep the forum tidy.
Interim method:
> Go to the first post in your thread. Click on "Edit Post". Now click on the orange "Go Advanced" button. In the advanced editor change the prefix to "SOLVED". Now click on the orange "Save Changes" button.

[INDENT][INDENT]keep on keep'n on[/INDENT][/INDENT]

---

### Post by woodsyboredom on 2013-07-10
OH no now I hav e similar problem with my desktop! I ran the command codes you suggested but I get these erroe messages at the end:

E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

as far as I know no other process is using it. I'll try with the internet down but I'm scared.

---

### Post by arpanaut on 2013-07-10
That error usually indicates that there is another package manager open,
If another manager is not open, try rebooting, then try your updates again.

---

### Post by claracc on 2013-07-11
> **arpanaut said:**
> That error usually indicates that there is another package manager open,
If another manager is not open, try rebooting, then try your updates again.

+1

Do you have synaptic manager open?. If so close it
Do you have software center open?. If so close it 
Then try again to update:

```
sudo apt-get update
```

---

