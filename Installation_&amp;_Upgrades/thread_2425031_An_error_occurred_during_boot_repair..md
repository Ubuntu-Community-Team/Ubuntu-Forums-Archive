---
title: "An error occurred during boot repair."
date: 2019-08-19
forum: Installation &amp; Upgrades
---

### Post by sunbear-c22 on 2019-08-19
After using boot repair, it told me I had an error. See [here]("http://paste.ubuntu.com/p/QpTZC8rxb9/") 

**Q1:** May i know what is the error and what I need to do?

I had used the **"**If Manjaro is not involved**"** procedure mentioned [here]("https://unix.stackexchange.com/a/273083"). I wanted to use `[COLOR=#000000]nvme0n1p3/etc/default/grub` instead of `[/COLOR][COLOR=#000000]sdb3/etc/default/grub` to be the default boot script.[/COLOR][COLOR=#000000]
[/COLOR]
Outcomes:
[LIST=1]
[*]I am able to use the [COLOR=#000000]nvme0n1p3[/COLOR]/etc/default/grub file to boot up.
[*][COLOR=#242729][FONT=Arial]Grub2 menu background turned greyish color and the background image that I had specified in /etc/default/grub failed to appear. Changes in video resolution were effected. [/FONT][/COLOR]
[*][COLOR=#242729][FONT=Arial]The grub2 Menu showed several EFI boot options which I did not have before and don't want them to appear. See  below.[/FONT][/COLOR]
[/LIST]

```

*Ubuntu
Advance options for Ubuntu 
EFI/BOOT/bkpbootx64.efi
EFI/BOOT/fbx64.efi
EFI/ubuntu/fbx64.efi
EFI/ubuntu/fwupx64.efi
EFI/ubuntu/mmx64.efi
Ubuntu 18.04.3 LTS (18.04) (on /dev/sdb3)
Advance options for Ubuntu 18.04.3 LTS (18.04) (on /dev/sdb3)
System setup

```

**Q2:**  How can I fix Outcome 2 and 3?

Thanks.


**UEFI Boot setup:**
Fast boot -- Disabled
CSM --Disabled
Secure Boot: State --                     Enabled
                    Platform key State -- Unloaded
                    OS Type --                Other OS

```

$ [ -d /sys/firmware/efi ] && echo "EFI boot on HDD" || echo "Legacy boot on HDD"
EFI boot on HDD

```

---

