---
title: "How to install flash in ubuntu"
date: 2011-08-15
forum: Installation &amp; Upgrades
---

### Post by cyan_01 on 2011-08-15
I am trying to install flash on my unbuntu:

% cat /etc/issue
Ubuntu 10.04.3 LTS \n \l

% uname -a
Linux cyanQEXen1Ubuntu 2.6.32-33-generic-pae #71-Ubuntu SMP Wed Jul 20 18:46:41 UTC 2011 i686 GNU/Linux


Here are the steps I used:

% sudo alien -k flash-plugin-10.3.183.5-release.i386.rpm 
error: incorrect format: unknown tag
Warning: Skipping conversion of scripts in package flash-plugin: postinst postrm prerm
Warning: Use the --scripts parameter to include the scripts.
flash-plugin_10.3.183.5-release-1_i386.deb generated

% sudo dpkg -i flash-plugin_10.3.183.5-release-1_i386.deb 
[sudo] password for qe: 
Selecting previously deselected package flash-plugin.
(Reading database ... 259270 files and directories currently installed.)
Unpacking flash-plugin (from flash-plugin_10.3.183.5-release-1_i386.deb) ...
Setting up flash-plugin (10.3.183.5-release-1) ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for desktop-file-utils ...
Processing triggers for python-support ...

How to correct the "unknown tag" error? Or what's the correct tag I should use?

I also tried this and got the same error:

sudo alien --to-deb flash-plugin-10.3.183.5-release.i386.rpm 
[sudo] password for qe: 
error: incorrect format: unknown tag
Warning: Skipping conversion of scripts in package flash-plugin: postinst postrm prerm
Warning: Use the --scripts parameter to include the scripts.
flash-plugin_10.3.183.5-1_i386.deb generated

I have googled for solutions but no luck. Please help, thanks.

---

### Post by lovinglinux on 2011-08-15
Why are you installing from a rpm package? Ubuntu uses deb packages, not rpm. Although you can convert them with alien, I bet that is the source of your problem.

Additionally, you can install flash from the repositories. Just search for flash in the Ubuntu Software Center or use the command below:

```
sudo apt-get install flashplugin-installer
```

You can also use my [Flash-Aid]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/") extension, which can install the latest Flash 11 Beta, remove conflicting plugins and apply some performance tweaks.

---

