---
title: "grub2/karmic kernel parameters for HP Mini"
date: 2009-12-06
forum: Installation &amp; Upgrades
---

### Post by fix.kowalski on 2009-12-06
Hello,

in order to have my HP Mini boot & work correctly with Karmic (fresh install), I use the following kernel parameters supplied by HP to operate the MIE (an HP Mini running a customized Ubuntu).

rootwait ht=on clocksource=hpet reboot=a acpi_os_name=Symphony acpi_osi=video_repost

Those parameters work just fine, avoiding a number of crashes (boot, wireless, ethernet deconnection, wake-up, ...etc).  However I still have a problem.

Jaunty & previous Ubuntu releases used grub1, where adding those supplemental parameters a generic fashion was easy (there was an prepared entry for this in /boot/grub/menu.lst).  Grub2 (used for fresh installs of Karmic) is another story...  I ended-up direct editing a shell script file, which seems very suboptimal to me (what will happen at next grub package upgrade?).  Here is my change:

    fi
    save_default_entry | sed -e "s/^/\t/"
    prepare_grub_to_access_device ${GRUB_DEVICE_BOOT} | sed -e "s/^/\t/"
    cat << EOF
-         linux   ${rel_dirname}/${basename} root=${linux_root_device_thisversion} ro $2
+         linux   ${rel_dirname}/${basename} root=${linux_root_device_thisversion} ro $2 rootwait ht=on clocksource=hpet reboot=a acpi_os_name=Symphony acpi_osi=video_repost
  EOF
    if test -n "${initrd}" ; then

Anyone here having a cleaner place to put these extra boot parameters?

Thanks

--FiX

---

