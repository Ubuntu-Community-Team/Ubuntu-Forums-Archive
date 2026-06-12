---
title: "Use Nvidia driver with Lucid live session"
date: 2010-12-11
forum: Installation &amp; Upgrades
---

### Post by amsterdamharu on 2010-12-11
Solved it, here is how I did it:
                     p { margin-bottom: 0.08in; }  [COLOR=#ff0000][SIZE=3]You need:[/SIZE][/COLOR]
 
[LIST=1]
[*]About 1G usb stick
[*]A computer that can boot off that     stick
[*]I got the mint iso     "linuxmint-9-gnome-cd-i386.iso" but the i386 Lucid iso     would work just the same I assume
[*]About 4G of free space
[*]A working Linux (I used mint 8)     kernel is importaint for re creating the squasfs but not sure what     version is needed but 9.04 or 9.10 Ubuntu would work just as well.
[*]A computer with an nvidia graphics     card that has working drivers for it.
[*]I assume all the commands are executed when logged in as a     normal user that can execute sudo.
[/LIST]
 
[COLOR=#ff0000][SIZE=3]Install the programs we need:[/SIZE][/COLOR]
```
sudo apt-get install unetbootin squashfs-tools
```[COLOR=#ff0000][SIZE=3]Make bootable iso with Lucid[/SIZE][/COLOR]
Now we get the iso file on your usb, 
Plug in a fat32 formatted usb drive (todo: maybe give the commands to do so here)
press alt + F2 and type unetbootin
After filling out your password it should show the unetbootin window
Check "Diskimage" ->  the ... button next to "diskimage" all the way on the right -> browse to where the iso is and select it -> in the bottom middle you should see your usb drive (mine is called /dev/sdb1) -> click OK.
After it is done extracting the iso files to usb and making it bootable it will ask you to restart, you can do so.

[COLOR=#ff0000][SIZE=3]Booting up the usb Lucid (first time)[/SIZE][/COLOR]
I assume it will boot up as the live CD, if it doesn't you might check your bios settings for usb boot settings. Most laptops have F1 or F9 to go to a boot menu, my desktop has escape to go to boot menu. Some computers have no boot menu and you have to check bios settings for boot order.
When it is done booting it might give you an error that low graphics mode is selected, click ok and choose "restart x" (not sure if this is a Mint thing or Ubuntu)
Now that you see your desktop you can wait a while and a message will pop up saying that you can install drivers for your videocard, do this but when it's done **don't reboot**.

[COLOR=#ff0000][SIZE=3]Copy the nvidia deb driver packages to your local system[/SIZE][/COLOR]
After it's installed copy the deb files to your local system.
For smarties you have to copy the deb files in /var/cache/apt/archive to (your local system)/home/your_user/temp/nvidia (all lower case)
More help: open nautilus (the file browser) and mount the home folder of your installed system (the old mint 8 or Ubuntu 9.04 9.10 on your harddisk). To do this you can click on the monitor icon on the top of the nautilus screen. Here are listings like "160 20GB Hard Disk 87GB filesystem" this happens to be my home so I double click on it which mounts it.
Press alt + F2 and type 
```
gksu nautilus
```Now you have nautilus as root, on the left side is the mounted local filesystem (now called a very long number which is the guid). Click on it and browse to the home of your locally installed system (the home of the user you usually log in with). Create a folder in your home called temp (lover case) -> in this folder create a folder named nvidia open this folder.
On the left side of the window is a clickable item named "File system" right click and choose "open in new tab" now browse to /var/cache/apt/archive and select all the files ending with .deb -> press control + c to copy -> go to the other tab having your local file systems home/youruser/temp/nvidia dir and paste the debs in there.
(Todo: use "sudo nvidia-xconfig" to create an /etc/X11/xorg.conf and put that in the chrooted squashfs under /etc/X11/xorg.conf )

[COLOR=#ff0000][SIZE=3]Re configure the squashfs[/SIZE][/COLOR]
Now you can reboot your system and boot in your mint 8/ubuntu 9.04/9.10. 
First we get the filesystem.squashfs, it is on your usb driver under the casper directory, copy that to your home under temp/sqfs (create sqfs directory under temp).
Open up a terminal and type the following command (this will take some time to complete):
```
sudo cd ~/temp/sqfs
sudo unsquashfs filesystem.squashfs

```After that's done you can type something like sudo ls, it's just to let it ask for your password so the following commands can complete without asking. Soon after that copy and paste the following commands (you can copy all the lines at once not line for line) in the terminal you just unsquased the squashfs and typed a sudo command in:
```
sudo cp ../nvidia/*.deb /var/cache/apt/archives/
sudo cp /etc/resolv.conf squashfs-root/etc/
sudo cp /etc/hosts squashfs-root/etc/
sudo mount --bind /dev/ squashfs-root/dev
sudo chroot squashfs-root # squashfs-root is the name of the extracted squashfs root dir
mount -t proc none /proc
mount -t sysfs none /sys
mount -t devpts none /dev/pts
export HOME=/root
export LC_ALL=C
dbus-uuidgen > /var/lib/dbus/machine-id
dpkg-divert --local --rename --add /sbin/initctl
ln -s /bin/true /sbin/initctl
apt-get install nvidia-current nvidia-settings

```That installed the nvidia drivers (chroot means the terminal is running the squashfs Lucid/mint 9 system not the locally installed system).
If you wish you could install some other things with apt-get like "apt-get install ffmpeg" but this is optional and the more you install the more space you'll need on the usb.
Time to clean up and re-create the squashfs file; copy and paste the following commands:
```
aptitude clean
rm -rf /tmp/* ~/.bash_history
rm /etc/resolv.conf
rm /etc/hosts
rm /var/lib/dbus/machine-id
rm /sbin/initctl
dpkg-divert --rename --remove /sbin/initctl
umount /proc # if this doesn't work try umount -lf /proc
umount /sys
umount /dev/pts
exit
```And at last one more command:
```
sudo umount squashfs-root/dev
```Now re create the squashfs, do replace myuser with your user (this will take a while):
```
sudo mksquashfs squashfs-root new_filesystem.squashfs 
sudo chown myuser:myuser new_filesystem.squashfs 
```[COLOR=#ff0000][SIZE=3]Create a cd directory to be used for the iso later[/SIZE][/COLOR]
Copy all the files from the Lucid or Mint iso file (I use linuxmint-9-gnome-cd-i386.iso) to ~/cd (including the hidden ones). 
To do this you can open a file browser and browse to the iso file, right click it and open with archive mounter -> in the left the iso is mounted as a cd click on it and you'll see the contents -> press control + h (there are hidden files on the cd that will show now) -> select all the files (control + a ) -> press control + c ( copy ) -> go to your home folder and create a folder named cd (lower case) -> go in this folder and press control + v

[COLOR=#ff0000][SIZE=3]Edit the start menu of the CD so nouveau drivers aren't loaded (they block nvidia)[/SIZE][/COLOR]
Go to the cd directory in your home folder and locate the file called isolinux.cfg (it is in your home/cd/isolinux directory). Open this up in a text editor. For Mint 9 you will see the following line:
```
  append  file= .....
```Replace this line with:
```
  append  file=/cdrom/preseed/mint.seed boot=casper initrd=/casper/initrd.lz nouveau.modeset=0 rdblacklist=nouveau blacklist=vga16fb nouveau.noaccel=1 --
```Save the file.

[COLOR=#ff0000][SIZE=3]Create a bootable iso[/SIZE][/COLOR]
Open a terminal and copy and paste the following commands:
```
cd ~
rm cd/casper/filesystem.squashfs
cp temp/sqfs/new_filesystem.squashfs cd/casper/filesystem.squashfs
mkisofs -pad -l -r -J -v -V "Ubuntu nvidia" -no-emul-boot -boot-load-size 4 -boot-info-table -b isolinux/isolinux.bin -hide-rr-moved -o boot.iso cd
```[COLOR=#ff0000][SIZE=3]Create bootable usb with changed squashfs and boot menu.[/SIZE][/COLOR]
Now we get the iso file on your usb, 
Plug in a fat32 formatted usb drive (todo: maybe give the commands to do so here)
press alt + F2 and type unetbootin
After filling out your password it should show the unetbootin window
Check "Diskimage" ->  the ... button next to "diskimage" all the way on the right -> [COLOR=#ff0000]**browse to your home folder and select boot.iso**[/COLOR] -> in the bottom middle you should see your usb drive (mine is called /dev/sdb1) -> click OK.
[COLOR=#ff0000][SIZE=1]**It will ask you to overwrite select all**[/SIZE][/COLOR]. After it is done extracting the iso files to usb and making it bootable it will ask you to restart, you can do so.


If you don't get a desktop at first press control + alt + F1 and type the following commands:
```
sudo nvidia-xconfig
sudo service gdm stop
sudo service gdm start
```This is because I haven't got time yet to update this manual and put the xorg.conf in the chrooted system before re creating the squashfs.


If you have any questions please don't hesitate to ask them, the only stupid question is a question unasked.

---

### Post by efflandt on 2010-12-11
There is no way to use the nvidia proprietary drivers from the live/install iso, even when on USB with persistent data (unless you roll your own iso first).  It boots a fixed squashfs file system before persistent data (if present) is mounted.  So the kernel and other things that happen during boot cannot be changed or updated from Synaptic or with a simple apt-get command.

If you do a regular install to usb ( >=8 GB recommended, 4 GB might work with not much room to spare) you can add video drivers and do any updates.  But you have to make certain that you know how to put grub on the mbr of your usb device instead of default to main internal drive mbr.  In Lucid (10.04) or earlier install, grub location is selected from **Advanced** button in the summary screen after you set your user info.  In Maverick you need to use manual partitioning and look at the bottom of that screen to select where to put grub.

---

### Post by amsterdamharu on 2010-12-11
Thank you for your reply. I was afraid of this replay and have 2 questions as to why this is not a bug.
1. A kernel module can be loaded dynamically so why does it require a reboot?
2. If many people suggest to try out an ubuntu release then why is one important part (descent graphics) something that cannot be tested. I have no guarantee that the nvidia card (or any driver that requires a reboot) will actually work with Lucid.

Tried to apt-get install nvidia-common in the chrooted system and then rebuild the squasfs -> iso -> usb but it would only give me the same error on startup saying nvidia module not loaded.

Still need to gamble installing Lucid and see if this problem is resolved in a reboot.

Writing this from the fully updated webcam and soundcard (yes with recording) working Lucid but graphics are total crap, can hardly read what I am typing here.

---

### Post by amsterdamharu on 2010-12-13
I still don't get it. Tried checking the initrd but only thing I could find is something that will overwrite the xorg.conf if xforcevesa is used. The xorg.conf I have on a fresh boot is the one nvidia-xconfig came up with.

After installing in the chrooted system all the modules are present so they are in the re created squashfs.

When booting into live and re installing the driver nothing in boot directory is changed (initrd or kernel files). So why do I need a reboot?

How can I customize this live CD with a working nvidia driver?
[https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization) (look for nvidia)
It used to work just restarting x but seems to be broken somehow. 

Just afraid that a full install will just end up giving me the same problem and after a reboot it will just tell me nvidia module not loaded and end up with a worthless system.

---

### Post by amsterdamharu on 2010-12-13
I am at a loss now, added the following to the /etc/modprobe.d/blacklist.conf 
```
# added this for nvidia driver to work, once nouveau is loaded nvidia never wor$
blacklist nouveau
blacklist lbm-nouveau
blacklist nvidia-173
blacklist nvidia-96
```

Then re created the squashfs and just booted off it, the blacklist.conf has the values added to it so that went right but when running lsmod I get:
```
Module                  Size  Used by
binfmt_misc             6587  1 
lp                      7028  0 
dm_crypt               11331  0 
snd_hda_codec_realtek   203168  1 
snd_hda_intel          21877  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
ppdev                   5259  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
parport_pc             25962  1 
psmouse                63245  0 
parport                32635  3 lp,ppdev,parport_pc
serio_raw               3978  0 
k8temp                  3024  0 
snd                    54148  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               6620  1 snd
i2c_nforce2             5199  0 
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
squashfs               20680  1 
aufs                  149050  1 
nls_iso8859_1           3249  1 
nls_cp437               4919  1 
vfat                    8901  1 
fat                    47767  1 vfat
dm_raid45              81647  0 
xor                    15028  1 dm_raid45
fbcon                  35102  73 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
nouveau               467048  3 
ttm                    49943  1 nouveau
drm_kms_helper         29297  1 nouveau
drm                   162471  4 nouveau,ttm,drm_kms_helper
agpgart                31724  2 ttm,drm
usb_storage            39425  1 
floppy                 53016  0 
i2c_algo_bit            5028  1 nouveau
ahci                   32008  1 
r8169                  33884  0 
mii                     4381  1 r8169
pata_amd                8766  0 
```

Cannot figure out what nouveau is doing in there when it's blacklisted.

This is all just way over my head and I think it's too soon for me to try Licid as it obviously needs some kinks to work out. I won't mind helping in doing so but where do I get help?
Everywhere I read that kernel modules can be loaded and unloaded without a reboot so the reboot is not needed, I also read that a loaded nouveau screws up nvidia and I am still unable to blacklist or unload it.

---

### Post by amsterdamharu on 2010-12-13
Should have searched more thorough, found that nouveau is loaded early.

Found it in the squasfs filesystem:
lib/modules/2.6.32-21-generic/kernel/drivers/gpu/drm/nouveau

Found it in the initrd that is in the squashfs filesystem:
lib/modules/2.6.32-21-generic/kernel/drivers/gpu/drm/nouveau

Found it in the initrd of the CD (/casper/initrd.lz)
live/lib/modules/2.6.32-21-generic/kernel/drivers/gpu/drm/nouveau 

Renamed all the nouveau.ko to nouveau.go.away.ko but now I have to hope that extracting and re building the initrd has gone well:

the initrd.lz on the cd:
```
# extract initrd
unlzma -c -S .lz ../initrd.lz | cpio -imvd --no-absolute-filenames
# create initrd, say all the files are in a directory called live
# now copy that to a folder (only containing live) go into that folder and use the follwing command:
find | cpio -o -H newc > ../newinitrd
# go up one directory
find . | cpio -o -H newc -V | lzma -7 > ../newinitrd.lz

```

The initrd.img-2.6.32-21-generic in the squashfs filesystem:
```
# extract 
sudo gunzip < ../initrd.img-2.6.32-21-generic | cpio -imvd --no-absolute-filenames
# create
find . | cpio -H newc -o > ../initrd.cpio
gzip ../initrd.cpio
mv ../initrd.cpio.gz ../new_initrd.img
```

If this works it takes some serious hacking to get an nvidia card to work in Lucid live. I remember choosing xforcevesa worked fine on my nvidia in Mint 8 (Ubuntu 9.10). After installing the drivers just logging in and out would be enough to have the driver working.

---

