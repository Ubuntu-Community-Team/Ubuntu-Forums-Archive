---
title: "Disk errors in syslog when Dapper upgrade fails"
date: 2006-06-03
forum: Installation &amp; Upgrades
---

### Post by Lemsip on 2006-06-03
I tried upgrading from Breezy (Kubuntu, although I use Gnome) to Dapper using the upgrade manager, and it failed with a message suggesting I try apt-get dist-upgrade.

So I tried that, and that also failed with
```

.....
Get:1546 http://us.archive.ubuntu.com dapper/main python-pisock 0.11.8-17 [31.6kB]
Get:1547 http://us.archive.ubuntu.com dapper/main python2.4-pycurl 7.15.0-1ubuntu1 [54.4kB]
Get:1548 http://us.archive.ubuntu.com dapper/main slocate 3.0.beta.r3-1 [30.1kB]
Get:1549 http://us.archive.ubuntu.com dapper/main xlibs-dev 7.0.0-0ubuntu45 [9028B]
Fetched 885MB in 1h5m0s (227kB/s)
Extracting templates from packages: 100%
Preconfiguring packages ...
E: Sub-process /usr/bin/dpkg exited unexpectedly
root@mercury:/root # 

```

I also noticed in syslog, the lots of messages like the following appeared:

```

Jun  3 23:27:13 localhost kernel: [4299885.209000] ide: failed opcode was: unknown
Jun  3 23:27:13 localhost kernel: [4299885.209000] end_request: I/O error, dev hda, sector 85646890
Jun  3 23:27:13 localhost kernel: [4299889.369000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Jun  3 23:27:13 localhost kernel: [4299889.369000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=85646899, high=5, low=1760819, sector=85646898
Jun  3 23:27:13 localhost kernel: [4299889.369000] ide: failed opcode was: unknown
Jun  3 23:27:13 localhost kernel: [4299889.369000] end_request: I/O error, dev hda, sector 85646898
Jun  3 23:27:17 localhost kernel: [4299893.930000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Jun  3 23:27:17 localhost kernel: [4299893.930000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=85646899, high=5, low=1760819, sector=85646898
Jun  3 23:27:17 localhost kernel: [4299893.930000] ide: failed opcode was: unknown
Jun  3 23:27:17 localhost kernel: [4299893.930000] end_request: I/O error, dev hda, sector 85646898
Jun  3 23:27:17 localhost kernel: [4299893.930000] Buffer I/O error on device hda9, logical block 335889
Jun  3 23:27:21 localhost kernel: [4299898.133000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Jun  3 23:27:21 localhost kernel: [4299898.133000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=85646899, high=5, low=1760819, sector=85646898
Jun  3 23:27:21 localhost kernel: [4299898.133000] ide: failed opcode was: unknown
Jun  3 23:27:21 localhost kernel: [4299898.133000] end_request: I/O error, dev hda, sector 85646898
Jun  3 23:27:21 localhost kernel: [4299898.133000] Buffer I/O error on device hda9, logical block 335889

```

Where it refers to hda9, this is my /var partition (reiserfs), and this partition (and the others on that drive) all otherwise appear to be working absolutely fine.  If I do a reboot, no errors come up relating to the drive.

My machine is a Dell Precision 820 (dual CPU).

Can anyone help?

---

### Post by catlett on 2006-06-03
I don't know if this will make any difference but I would try it again with a couple of small changes. First don't use a root terminal. Use a regular terminal as  user. Then use sudo to invoke root priveleges and use aptitude instead of apt-get. So since you have nothing to loose try ```
sudo aptitude update
``````
sudo aptitude dist-upgrade
```

---

### Post by Lemsip on 2006-06-03
Thanks for the quick response, Catlett.  I tried that, and it failed with:

```

......
Get:43 http://us.archive.ubuntu.com dapper/universe libgpod-common 0.3.2-0ubuntu1 [13.8kB]
Get:44 http://us.archive.ubuntu.com dapper/universe python-beagle 0.2.6-1ubuntu5 [43.9kB]
Get:45 http://us.archive.ubuntu.com dapper/universe python-serial 2.2-1 [37.4kB]
Fetched 89.3MB in 7m41s (194kB/s)
Extracting templates from packages: 100%
Preconfiguring packages ...
                12E: Sub-process /usr/bin/dpkg exited unexpectedly
Ack!  Something bad happened while installing packages.  Trying to recover:
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
neil@mercury:~$

```

...and lots more of the same kind of disk errors in syslog.

Hmmmm.....

---

### Post by Lemsip on 2006-06-04
Ok, upon further investigation using 'badblocks' I've found that actually my disk is on the way out, so this appears not to be a Dapper issue :)

Thanks!

---

