---
title: "Can not install any apps due to syntax error in grub.cfg file | Ubuntu 20.04"
date: 2022-07-16
forum: Installation &amp; Upgrades
---

### Post by at0m166 on 2022-07-16
Hi everyone,
I ran into this error while using "sudo update-grub"
> 
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-5.13.0-48-generic
Found initrd image: /boot/initrd.img-5.13.0-48-generic
Found linux image: /boot/vmlinuz-5.13.0-44-generic
Found initrd image: /boot/initrd.img-5.13.0-44-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Recovery Environment on /dev/sda1
error: out of memory.
error: syntax error.
error: Incorrect command.
error: syntax error.
Syntax error at line 329
Syntax errors are detected in generated GRUB config file.
Ensure that there are no errors in /etc/default/grub
and /etc/grub.d/* files or please file a bug report with
/boot/grub/grub.cfg.new file attached.

The grub.cfg.new file can be found here: [https://pastebin.com/pgiczCXZ](https://pastebin.com/pgiczCXZ)
. Now because of this error I can't install anything new. I'm so lost at where is wrong.
Any help would be much appreciated. Thanks for reading!

---

### Post by Impavidus on 2022-07-16
I've no idea where that out of memory message comes from, but I do notice a ; on line 327, but not on line 325. I don't think that ; is supposed to be there. Have a look at your /etc/grub.d/41_custom. Maybe you edited it and left a stray ;. For comparison, this is the /etc/grub.d/41_custom on my 22.04 system, which I didn't change from the default:```
#!/bin/sh
cat <<EOF
if [ -f  \${config_directory}/custom.cfg ]; then
  source \${config_directory}/custom.cfg
elif [ -z "\${config_directory}" -a -f  \$prefix/custom.cfg ]; then
  source \$prefix/custom.cfg
fi
EOF

```

---

### Post by at0m166 on 2022-07-16
Thanks for your help @Impavius. It turned out that I need to use (sudo chmod -x /etc/grub.d/41_custom) and (sudo chmod +x /etc/grub.d/30_os-prober) then try (sudo update-grub) command. Hope this would help anyone having same issue in the future.

---

### Post by oldfred on 2022-07-16
Your 40_custom
line 313 only one double quote
 line 314 has par_msdos which should be part_msdos 
line 316 And a set root with one quote 

Or your Windows boot stanza that you manually added is not correct at all.

---

