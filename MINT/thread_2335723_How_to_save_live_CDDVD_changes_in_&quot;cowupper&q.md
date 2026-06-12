---
title: "How to save live CD/DVD changes in &quot;/cow/upper&quot; to persistent storage"
date: 2016-08-31
forum: MINT
---

### Post by jdb2 on 2016-08-31
I've been running Linux Mint 17.3 Cinnamon 64-bit for a while on an external USB 3.0 SSD, and, recently, my system crashed ( I know I'm running Linux Mint but the casper init/boot scripts are pretty much identical to the Ubuntu ones ). Since then, I've been recovering my data via a Linux Mint live CD/DVD containing the same version of Linux Mint that I mentioned previously. The problem is that I did not give the kernel the "persistent" argument when I booted into the live environment and there are no casper-rw partitions or files containing persistent data. This is a major problem as I need to preserve the changes on the live CD/DVD as I need to reboot the system under question. I know how to save the changes, using a method similar to [this]("http://davstott.me.uk/index.php/2013/09/05/ubuntu-13-04-on-a-usb-flash-drive-and-merging-its-persistent-storage/"), except, that the linked method won't work for me as I have no preexisting casper-rw partition or file, at least one that isn't empty. I've been examining the casper boot/init scripts and the code that seems to mount the root overlayfs filesystem is :

```
overlay|overlayfs)
            # Mount the layers pairwise from the bottom onto rootmnt,
            # for the second and later layers rootmnt forms the lower layer.
            mounts=""
            for mount in /cow $rofslist
            do
                mounts="$mount $mounts"
            done
            lower=""
            for mount in $mounts
            do
                if [ "$lower" = "" ]; then
                    lower="$mount"
                    continue
                fi
                mount -t ${UNIONFS} -o "upperdir=$mount/upper,lowerdir=$lower,workdir=$mount/work" \
                    "$mount" "$rootmnt" || \
                  mount -t ${UNIONFS} -o "upperdir=$mount/upper,lowerdir=$lower" \
                      "$mount" "$rootmnt"
                lower="$rootmnt"
            done
            ;;
    esac
```

The problem is that I need to gain access to /cow/upper ( the only place that I know of where it's even displayed is in /proc/mounts ), but, /cow/upper isn't in the overlayfs root filesystem. It would seem to me that the casper boot/init scripts would need to set up a chroot environment after having mounted the overlayfs filesystem, but, I can't the find the place in the casper scripts, if it exists, where the chroot is set up. If there is a chroot, then, I could use a method similar to the one described [here]("http://www.unixwiz.net/techtips/mirror/chroot-break.html") to break out of it and gain access to /cow/upper.

Any help would be appreciated.

Thanks,

jdb2


EDIT : I know I could use rsync or cp with exclusions to create a new squashfs image, but, if there's a way to access /cow/upper and do it the "right way", then I'd rather do it that way.

---

### Post by howefield on 2016-08-31
Thread moved to the "*MINT*" sub forum.

---

