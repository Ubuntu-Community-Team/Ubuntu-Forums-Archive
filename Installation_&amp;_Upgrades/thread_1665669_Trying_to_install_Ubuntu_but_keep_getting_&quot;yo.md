---
title: "Trying to install Ubuntu but keep getting &quot;you need to load the kernel first&quot;"
date: 2011-01-12
forum: Installation &amp; Upgrades
---

### Post by saxon78 on 2011-01-12
Hi all, I'm new to Linux and have just downloaded the windows installer. I've installed it via windows to my C: partition so I have C:/ubuntu

Now when I reboot to complete the installation, I choose ubuntu from the boot menu, it counts down and then comes up with the following error.

"could not locate file, you need to load the kernel first"

Any ideas anyone?

Here's the contents of the grub.cfg file if that helps.....

> #This file is modified at runtime by bootmenu.nsh

set default=0
echo "Completing the Ubuntu installation."
echo "For more installation boot options, press `ESC' now..."
if sleep --verbose --interruptible 5 ; then
   set timeout=0
fi
echo

# TBD try to boot directly from kernel/initrd within the ISO via the grub2 loop module

search -s -f -n /ubuntu/install/boot/vmlinuz

menuentry "Normal mode" {
    linux /ubuntu/install/boot/vmlinuz debian-installer/custom-installation=/ubuntu/install/custom-installation iso-scan/filename=/ubuntu/install/installation.iso automatic-ubiquity noprompt quiet splash  boot=casper ro debian-installer/locale=en_GB.UTF-8 console-setup/layoutcode=gb console-setup/variantcode= --  rootflags=syncio
    initrd /ubuntu/install/boot/initrd.lz
}

menuentry "Safe graphic mode" {
    linux /ubuntu/install/boot/vmlinuz debian-installer/custom-installation=/ubuntu/install/custom-installation iso-scan/filename=/ubuntu/install/installation.iso automatic-ubiquity noprompt debug debug-ubiquity xforcevesa boot=casper ro debian-installer/locale=en_GB.UTF-8 console-setup/layoutcode=gb console-setup/variantcode= --   rootflags=syncio
    initrd /ubuntu/install/boot/initrd.lz
}

menuentry "ACPI workarounds" {
    linux /ubuntu/install/boot/vmlinuz debian-installer/custom-installation=/ubuntu/install/custom-installation iso-scan/filename=/ubuntu/install/installation.iso automatic-ubiquity noprompt debug debug-ubiquity boot=casper ro debian-installer/locale=en_GB.UTF-8 console-setup/layoutcode=gb console-setup/variantcode= --   rootflags=syncio acpi=off noapic nolapic
    initrd /ubuntu/install/boot/initrd.lz
}

menuentry "Verbose mode" {
    linux /ubuntu/install/boot/vmlinuz debian-installer/custom-installation=/ubuntu/install/custom-installation iso-scan/filename=/ubuntu/install/installation.iso automatic-ubiquity noprompt debug debug-ubiquity boot=casper ro debian-installer/locale=en_GB.UTF-8 console-setup/layoutcode=gb console-setup/variantcode= --   rootflags=syncio
    initrd /ubuntu/install/boot/initrd.lz
}

menuentry "Demo mode" {
    linux /ubuntu/install/boot/vmlinuz iso-scan/filename=/ubuntu/install/installation.iso quiet splash boot=casper ro debian-installer/locale=en_GB.UTF-8 console-setup/layoutcode=gb console-setup/variantcode= --  rootflags=syncio
    initrd /ubuntu/install/boot/initrd.lz
}


---

