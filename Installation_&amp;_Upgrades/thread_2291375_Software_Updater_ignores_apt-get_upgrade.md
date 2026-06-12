---
title: "Software Updater ignores apt-get upgrade?"
date: 2015-08-19
forum: Installation &amp; Upgrades
---

### Post by Tim_Johnson on 2015-08-19
I'm using lubuntu 14.04 on a netbook.
If I run the following from a terminal: ```

sudo apt-get update
sudo apt-get upgrade 
```
Showing a successful upgrade, and then repeat the commands
I see the following : ```

sudo apt-get upgrade
[sudo] password for tim:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.13.0-24 linux-headers-3.13.0-24-generic
  linux-image-3.13.0-24-generic linux-image-extra-3.13.0-24-generic
Use 'apt-get autoremove' to remove them.
The following packages have been kept back:
  linux-generic linux-headers-generic linux-image-generic
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
```
Now, I see that **Software Updater** has been loaded in my gui.
I close Software Updater and restart it, to make sure that all system data that it 
has access to has been updated.
Still Software Updater is telling me that ```

Update Software is available for this computer ... 
```
When apt-get tells me that no further upgrade is needed.

Why is that?
Thanks
tim

---

### Post by Bashing-om on 2015-08-19
Tim_Johnson; Hello;

I do not use the GUI updater, so can not directly advise; however:
> 
[color=green]The following packages have been kept back:[/color]
  linux-generic linux-headers-generic linux-image-generic
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.

'apt-get update' will not install new packages. In this instance we need a different tool to install the held packages. That tool is "dist-upgrade" .
Try as :
```

sudo apt-get dist-upgrade

```
to install the new kernel.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by Tim_Johnson on 2015-08-19
Bashing-om : I believe I understand you. I'm moving towards console usage only myself, but was trying to resolve the differences and I believe that you have helped.
I've also run 'auto-remove' and rebooted. I now longer get signaled by Software Update.

Can you please sum up the commands that you use to keep updated?

Also, how do I know when the computer needs to be rebooted after an upgrade?
(I'm like to have all of this handled by cron someday).

Thank you
Tim

---

### Post by Bashing-om on 2015-08-19
Tim_Johnson; Sure !

For updating:
I use the new revamped 'apt' :
```

sudo apt update
sudo apt upgrade

``` The new 'apt' WILL install new packages as it does incorporate ' apt-get dist-upgrade''s smart mode.
In some cases
```

sudo apt full-upgrade

```
might be required.

To check package manager status after a period of time:
```

sudo apt get clean
sudo apt-get autoclean
sudo apt-get autoremove
sudo apt-get -f install
sudo dpkg -C

```
Paying attention to what 'autoremove' is going to remove before pulling the trigger. In a dynamic system - though I have never had a problem - I can see where the package status can get cross-wise.
[https://www.debian.org/doc/manuals/debian-reference/ch02.en.html#_debian_package_management_prerequisites](https://www.debian.org/doc/manuals/debian-reference/ch02.en.html#_debian_package_management_prerequisites)

If there is a major change in the system, such as booting up on the new kernel, then a reboot is required. I do understand that in the future this will no longer be required (!)  I am going to manually reboot anyway and pay attention to what the system tells me.

Upfront. I am terminal minded - I did come up in this world before a GUI was. I boot my system to terminal, Then if I want a GUI I start the GUI from terminal. My box is an old dual core Athlon system and I boot up in @5 seconds from a cold boot !
I want to look at boot messages rather than a pretty picture as I boot .

[INDENT][INDENT]get'r done
[/INDENT][/INDENT]

---

### Post by Tim_Johnson on 2015-08-19
Thank you. Awesome to get such quick and succint response. Marking solved...

---

### Post by Bashing-om on 2015-08-19
Tim_Johnson; :)

Enjoy

Come back anytime .

[INDENT][INDENT][INDENT]good things do happen
[/INDENT][/INDENT][/INDENT]

---

### Post by ian-weisser on 2015-08-19
> **Tim_Johnson said:**
> (I'm like to have all of this handled by cron someday).

The work is already done for you. See the 'unattended-upgrades' package.
Also see the already-existing daily apt update script at /etc/cron.daily/apt

---

### Post by Tim_Johnson on 2015-08-19
> **ian-weisser said:**
> The work is already done for you. See the 'unattended-upgrades' package.
Also see the already-existing daily apt update script at /etc/cron.daily/apt

Thank you!

---

