---
title: "KVM disk (virtio) performance pathetic - need help"
date: 2015-12-29
forum: MINT
---

### Post by heiko_s on 2015-12-29
OK, so I managed to install Windows 10 using OVMF UEFI on my Samsung EVO 850 SSD using LVM. Under Xen LVM works superb and I achieved practically native disk I/O performance. Below are the Passmark 8 results:

[IMG]http://www.pbase.com/merhav/image/162215834/original.jpg[/IMG]


The Xen PV result right above my qemu-kvm benchmark is from my previous Xen Windows 7 VM, but using a different SSD (Sandisk Extreme 120GB).

Here is the qemu start command I used to get the results shown in the picture: 

```
qemu-system-x86_64 \
  -name $vmname,process=$vmname \
  -cpu host,kvm=off \
  -smp 10,sockets=1,cores=5,threads=2 \
  -enable-kvm \
  -m 20G \
  -mem-path /dev/hugepages \
  -mem-prealloc \
  -balloon none \
  -rtc clock=host,base=utc \
  -vga none \
  -nographic \
  -serial null \
  -parallel none \
  -device vfio-pci,host=02:00.0,multifunction=on \
  -device vfio-pci,host=02:00.1 \
  -device vfio-pci,host=00:1a.0 \
  -device vfio-pci,host=08:00.0 \
  -drive if=pflash,format=raw,readonly,file=/usr/share/edk2.git/ovmf-x64/OVMF_CODE-pure-efi.fd \
  -drive if=pflash,format=raw,file=/tmp/my_vars.fd \
  -boot order=c \
  -device virtio-scsi-pci,id=scsi \
  -drive id=disk0,if=virtio,cache=none,format=raw,file=/dev/mapper/lm13-win10 \
  -drive id=disk1,if=virtio,cache=none,file=/dev/mapper/photos-photo_stripe \
  -drive id=disk2,if=virtio,cache=none,file=/dev/mapper/media-photo_raw \
  -net nic,model=virtio,macaddr=00:16:3e:00:07:07 -net tap

```

Hardware:
i7 3930K 6-core CPU
32GB memory, 20GB for the Windows VM
A bunch of harddrives paired in 2 with striped LVM.

Software:
Ubuntu 14.04 (Linux Mint 17.3)
QEMU emulator version 2.1.2
edk2.git-ovmf-x64-0-20151222.b1393.gff3b043.noarch

VM:
Windows 10 Professional 64bit
virtio-win-0.1.112 (latest) - the following drivers are installed:
NetKVM/: Virtio Network driver
viostor/: Virtio Block driver
vioscsi/: Virtio SCSI driver


Remarks:
Windows recognizes the SSD as such and doesn't perform optimization.

I've tried some options under kvm, but the results were questionable. With
```
#-global virtio-blk-pci.physical_block_size=512 \
#-global virtio-blk-pci.logical_block_size=512 \

``` I could see some improvement in read times when I mounted the SSD only, but once I added the other drives performance plummeted.

I'm not familiar with kvm and the tuning tips [http://www.linux-kvm.org/page/Tuning_KVM]("http://www.linux-kvm.org/page/Tuning_KVM") are pretty useless to me.

I also tried these options: [http://ubuntuforums.org/showthread.php?t=2289210&p=13334367#post13334367]("http://ubuntuforums.org/showthread.php?t=2289210&p=13334367#post13334367")
Unfortunately the disk specs didn't work and adding "-device scsi-hd,drive=disk0" would prevent the VM from starting. I didn't try it with "-machine type=pc-i440fx-2.1,accel=kvm", should I?

kvm is very confusing and the documentation isn't helpful either.  Can someone point me in the right direction?

---

### Post by howefield on 2015-12-29
Thread moved to the "*MINT*" forum.

---

