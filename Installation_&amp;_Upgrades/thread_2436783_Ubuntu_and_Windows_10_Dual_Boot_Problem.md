---
title: "Ubuntu and Windows 10 Dual Boot Problem"
date: 2020-02-13
forum: Installation &amp; Upgrades
---

### Post by anspectrum on 2020-02-13
First of all I must say that my _dual boot is working using EasyBCD_. However, I would like to get rid of this third part app and use Ubuntu native grub loader for this purpose. Below is an objectified version of whats the situation:

1. Partition Table:
```

Device     Boot     Start       End   Sectors   Size Id Type
/dev/sdb1  *         2048   1126399   1124352   549M  7 HPFS/NTFS/exFAT            // Windows 10 Auto-created boot partition
/dev/sdb2         1126400 153602047 152475648  72.7G  7 HPFS/NTFS/exFAT     //Windows 10 Installation partition
/dev/sdb3       153602048 204802047  51200000  24.4G 83 Linux                         //Ubuntu Installation partition
/dev/sdb4       204802048 500117503 295315456 140.8G  5 Extended
/dev/sdb5       204804096 212996095   8192000   3.9G 82 Linux swap / Solaris
/dev/sdb6       212998144 500117503 287119360 136.9G  7 HPFS/NTFS/exFAT
```

2. Block IDs

```
/dev/sda1: LABEL="New Volume" UUID="F632697B326941AB" TYPE="ntfs" PARTUUID="a11cac6d-02"
/dev/sdb1: LABEL="System Reserved" UUID="F660F7AC60F7722B" TYPE="ntfs" PARTUUID="0ba4d493-01"
/dev/sdb2: UUID="1C360FF5360FCF28" TYPE="ntfs" PARTUUID="0ba4d493-02"
/dev/sdb3: UUID="a993a479-c088-4f75-b0d4-a2c4a29d63aa" TYPE="ext4" PARTUUID="0ba4d493-03"
/dev/sdb5: UUID="2f4d3e27-ec6a-4d01-b308-ea51f6ff6367" TYPE="swap" PARTUUID="0ba4d493-05"
/dev/sdb6: UUID="7C62D0856A71A0B0" TYPE="ntfs" PARTUUID="0ba4d493-06"
```

3. Ubuntu Grub Entry in grub.cfg

```
menuentry 'Windows 10 (loader) (on /dev/sdb1)' --class windows --class os $menuentry_id_option 'osprober-chain-F660F7AC60F7722B' {
    insmod part_msdos
    insmod ntfs
    set root='hd1,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  F660F7AC60F7722B
    else
      search --no-floppy --fs-uuid --set=root F660F7AC60F7722B
    fi
    parttool ${root} hidden-
    drivemap -s (hd0) ${root}
    chainloader +1
}
```

4. Problem Nature:

I installed Win-10 first and Ubuntu later (well the order of installation does not really matter in this case). Ubuntu created the necessary loader entry as depicted in point 3. _**The problem is when I choose Win-10 to boot, I get sketchy Ubuntu screen like transitioning phase from Ubuntu to Win-10. The machine remains in this state, though not halted as I can see keys (like CAPS-LOCK) still responding**_. After this I used Win-10 bootable USB (well Ive made bootable Win-10 and Ubuntu USB) to fix Win-10 boot loader and as expected Ubuntu loader was removed.

5. Fixing using EasyBCD:

While in Windows, installed EasyBCD and created second entry for Ubuntu in its menu. After this I was able to boot into either Win-10 or Ubuntu. Later in Ubuntu, I re-installed grub in MBR.

6. Current Situation:

Machine boots using Ubuntu loader and I can choose either Ubuntu or Win-10. If I choose Win-10, The control is handed over to the menu entries created using EasyBCD (I can see that if I put a little bit of delay in EasyBCD entries menu). If I remove EasyBCD Win-10 entry, again I am unable to boot into Win-10.

7. What I am aiming for:

Native Ubuntu grub loader to boot Ubuntu or Win-10 without using EasyBCD (or other third party tools). My dual boot setup had been working just fine while I was using Win-7 or even Win-XP alongwith Ubuntu in dual boot fashion. Seems like Win-10 has changed things a bit.

Please suggest what I can try. Sorry for a bit long post but hopefully it will be beneficial for others as well in the future.

---

### Post by oldfred on 2020-02-13
Is issue really Windows 10's fast start up?
Grub only boots working Windows, or Windows that is not hibernated. I think using EasyBCD then becomes a work around to boot Windows when hibernated & then it uses the very old grub4dos to boot Ubuntu, usually using an install of grub in a partition table PBR, not drive's MBR. If you have two drives Windows boot loader can be in Windows drive and grub in other drive's MBR whether Ubuntu is on that drive or not.

Unless very old system, you are showing BIOS/MBR configuration. Microsoft has required vendors to install in UEFI/gpt mode since Windows 8 released in 2012. The offer BIOS/MBR configuration more for those that have or now had Windows 7 and older systems and wanted all systems booting in BIOS mode.

       Fast Start up off (always on hibernation), note that Windows turns this back on with updates, SHIFT + Shut down button
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

Because Windows 10 turns fast start up back on & then grub will not boot Windows, it is inconvenient to dual boot Windows 10 in BIOS mode on one drive. With UEFI you can always boot Windows from UEFI boot menu when grub cannot boot it. And often then can fix Windows. But still best to have Windows repair/recovery flash drive to repair Windows & your Ubuntu live installer.

With BIOS and one drive, so only one MBR, you that to temporarily install Windows boot loader to turn off fast start up or make other repairs. Then restore grub to dual boot.

---

### Post by anspectrum on 2020-02-13
Hey Oldfred, glad to find you :)

My Win-10 fast boot is disabled. Hibernation is still on but I know I am cleanly shutting down Windows.
Yes, I've two physical drives. One is SSD where Ive Windows and Ubuntu and other one is normal HDD for data / backups. In HDD I can also see a small folder and a file in there which I think EasyBCD created for boot. However, I accessed /dev/sdb1 (which is System Reserved) and I can see all the relevant BCD related files / folders in there.

I am somewhat aware of UEFI based partitoning and filesystem advantages but for that I needed to do reinstallation of Ubuntu, which I don't wanna do (at least right now) as I've many programs installed and tuned as per my requirements. But if that is the only way forward I might do that as well.

My laptop is HP Elitebook Folio 9480m (I think its 2012 release) with 8GB RAM and 4th Gen i7 processor. I don't think its the limitation here.

My only concern is that if EasyBCD (or other third party tools) can do it, can't it be done with native Ubuntu loaders.
[COLOR=#008000]*(I am writing this reply on a different machine, I will be happy to share any info / output (including EaseBCD diagnostic menu entries) from dual boot laptop to move forward)*[/COLOR]

---

### Post by Frogs Hair on 2020-02-13
I'm an Easy BCD user and the main reason is that feature updates and major updates for Win 10 would not complete with grub and this was the case with two systems. Your results may vary though. When booting I see the current version of grub and If Win 10 is selected I get the metro boot loader. I have installed newer Ubuntu versions on both systems with no booting difficulties or repairs required.

---

### Post by anspectrum on 2020-02-13
Hey FrogsHair,

So essentially you are using EasyBCD for multibooting, right? 

I am doing the same but wanna get rid of it.

---

### Post by Frogs Hair on 2020-02-13
> **anspectrum said:**
> Hey FrogsHair,

So essentially you are using EasyBCD for multibooting, right? 

I am doing the same but wanna get rid of it.

Yes, and the Win 10 update problem on my systems is the reason. I have encountered the same problem with other Linux distributions also. You might not have that problem though. The grub customizer from the repo is a handy way to update changes in the grub script which can cause Win 10 boot issues.

---

