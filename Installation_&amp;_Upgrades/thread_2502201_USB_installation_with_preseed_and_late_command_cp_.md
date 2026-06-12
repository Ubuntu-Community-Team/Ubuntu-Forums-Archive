---
title: "USB installation with preseed and late_command cp fails"
date: 2024-11-05
forum: Installation &amp; Upgrades
---

### Post by pmortier on 2024-11-05
Dear all,
I have made a USB stick with the OS and a preseed.cfg file.
This runs fine, but in the last step I want to copy a file from my _USB_ stick _to_ the _HDD_.
I have tried several methods, but always fail with exit code 1.
The last command I tried was the following:[INDENT][COLOR=#0000ff]d-i preseed/late_command string \
for dev in $(ls /dev/sd?1); do \
mkdir -p /target/mnt/usb; \
mount -t auto $dev /target/mnt/usb && break; \
done; \
cp /target/mnt/usb/install-cli.sh /target/etc/install-cli.sh[/COLOR][/INDENT]

I also tried to copy to /target/home/user, which also fails.
Any help on this issue is much appreciated!

Best regards,
Peter

---

