---
title: "Autoinstall - Dual boot with Windows 10"
date: 2024-11-11
forum: Installation &amp; Upgrades
---

### Post by kaarejens on 2024-11-11
Hi,

I work for a company using Ubuntu LTS for developers, and we are using LVM and LUKS in a dual boot with Windows 10/11. Up until 22.04, this worked with manual installations, but as of 24.04, due to installer limitation, we are forced to work with autoinstall yaml configuration instead, due to our LVM setup.
I have been able to get a working LVM/LUKS configuration for pure Ubuntu machines, but when I try to do the same with Windows preinstalled, using preserve - the windows and EFI drives are preserved, but os-prober is not run (I guess since it is deactivated by default), and when activating os-prober after booting into the fresh install, no windows are detected by os-prober. 

How can I make autoinstall turn on os-prober and detect an UEFI installed windows partition?

I am not able to find any information on how to configure grub/os-prober, or how to correctly preserve windows in any official documentation, nor on google, so I hope someone here are able to help me. Any help would be greatly appreciated.

My current config looks like the following:

```

  storage:
    config:
      - id: disk-system
        type: disk
        ptable: gpt
        path: /dev/nvme0n1
        preserve: true        

      - id: part-efi
        type: partition
        number: 1
        device: disk-system
        size: 100M
        flag: boot
        grub_device: true
        preserve: true

      - id: msr-partition
        type: partition
        number: 2
        device: disk-system
        flag: msftres
        size: 16M
        preserve: true

      - id: part1
        type: partition
        number: 3
        device: disk-system
        grub_device: false
        size: 125358137856
        preserve: true

      - id: part-boot
        type: partition
        number: 4
        device: disk-system
        size: 1G

      - id: part-encrypted
        type: partition
        number: 5
        device: disk-system
        size: -1

      - id: dm-encrypted
        type: dm_crypt
        volume: part-encrypted
        key: "REDACTED"

      - id: vg-linsys
        type: lvm_volgroup
        name: linsys
        devices:
          - dm-encrypted

      - id: lv-swap
        type: lvm_partition
        name: swap
        size: 8G
        volgroup: vg-linsys

      - id: lv-root
        type: lvm_partition
        name: root
        volgroup: vg-linsys
        size: -1

      - id: format-efi
        type: format
        volume: part-efi
        fstype: fat32

      - id: format-boot
        type: format
        volume: part-boot
        fstype: ext4

      - id: format-root
        type: format
        volume: lv-root
        fstype: ext4

      - id: format-swap
        type: format
        volume: lv-swap
        fstype: swap

      - id: mount-root
        type: mount
        device: format-root
        path: /

      - id: mount-swap
        type: mount
        device: format-swap
        path: none

      - id: mount-boot
        type: mount
        device: format-boot
        path: /boot

      - id: mount-efi
        type: mount
        device: format-efi
        path: /boot/efi

```

---

### Post by grahammechanical on 2024-11-11
As a double check and to eliminate at least one possible cause - what state is Windows in? Fast Start Up on?

Regards

---

### Post by kaarejens on 2024-11-11
Thank you for your quick reply!

I have not checked this setting, but I assume it is in fast boot-up, as I  understand that is the default. I have basically just installed a  fresh win10 PRO, made sure bitlocker was disabled, rebooted into live  ubuntu 24 and used autoinstall. This has always worked flawlessly doing a manual install with the 22.04 ubuntu LTS, so I have never changed fast boot options previously, to make dual boot work. Could this affect os-probers ability to detect Windows?

I am looking for the correct way to actually activate os-prober (aside from doing a post-autoinstall sed/awk command on the 30-os-prober file, followed by update-grub or something like that) from within the autoinstall script (or a best practice for how to do this any other way combined with autoinstall), so this is run during install. But I see your point that doing this manually, also not working, would suggest something more is a miss. I just can't understand what.

I will test your fast startup tip, and see if that makes a difference, but if you or anyone else have made an autoinstall dual boot work, I would really love to see how you did it :) Any best practices in regard to this topic, would also be greatly appreciated!

Cheers,
Kaare

---

### Post by yancek on 2024-11-11
Having fast boot or hibernation on prevents Linux from mounting to access a windows filesystem.  It is a simple process to turn off/on as explained at the Microsoft site at the link below.

 [https://learn.microsoft.com/en-us/troubleshoot/windows-client/setup-upgrade-and-drivers/disable-and-re-enable-hibernation](https://learn.microsoft.com/en-us/troubleshoot/windows-client/setup-upgrade-and-drivers/disable-and-re-enable-hibernation)

---

### Post by qpkorr on 2024-12-06
Hi kaarejens,

Primarily - thank you - after lots of searching, yours is the first autoinstall.yaml file I've found that attempts a dual boot installation.  Much obliged!

Second - I was just wondering if you had any luck with your os-prober issue?

I'm hoping to put together an autoinstall file using btrfs and subvolumes - but I'm sure I'll be leaning heavily on your example to understand the dual boot aspects - but it would be nice if os-prober worked out of the box too!

Cheers,
John

---

### Post by kaarejens on 2024-12-06
Hi John,

I am sorry to say that I still am fighting this issue - just been to busy to give any updates or do extensive tests (which is very time consuming).

What looks to be the situation, is that autoinstall break the Windows boot mechanism/partition so that OS-prober can't detect it. 
I am able to mount and browse the windows partition from Ubuntu, so that part seems fine. But the windows  boot files seems damaged or corrupted. Disabling fast boot/hibernation did not solve the issue.

The only workaround so far, the one time I absolutely had to install 24.04 with dual boot, was to reinstall Windows, after autoinstall! Then Windows magically appeared and dual boot worked as intended. Much to my surprise. This is offcourse not a way forward (becuase it should never be done this way?) - though I have been playing with the thought of trying to use the Ubuntu-only autoinstall script we use, and then install Windows afterwards, as it actually went pretty smoothly. However, I am not happy with doing things in this way, and will spend some time ASAP, to get to the bottom of this issue.

I am shocked to say that you are the only other person I know off, that is also struggling with this - as google search, ai search and reference documentation search has gotton me nowhere and I see zero others complaining, which I find odd - so thank you for replying and showing me I am not the only one :D

I also have issues doing anything else but hardcode disk size, without getting int errors with autoinstall, which is therefor also another manual step in the process, as well as norwegian keyboard layout seems to be an issue (easily fixable post install, but it gives the feeling of autoinstall is fragile and not well supported). 
Having so many weird problems with autoinstall, lack off good documentation, and this sudden change away from enterprise best practise setup with the 24.04 installer (for what seems to be better bitlocker support?) are making us consider moving to debian, instead of spending so much time troubleshooting autoinstall and being afraid of what might be the next breaking change in the future :(  

The documentation from official Ubuntu sources on this topic seem to be non-existing, and the rest of autoinstall documentation is, in my opinion, also not up to par with what I expect for an enterprise OS.

I apologise for a little ranting, but this issue is taking my time and focus away from things like cyber security and compliance work with IEC and ISO standards, which makes me extremely frustrated. Forgive me :)

I will post updates, as soon as I have (hopefully) found a way for dual boot to work :) If anyone else has this already working, -_**please**_- let me and John know, because it is breaking my Ubuntu heart :)

Cheers!

---

