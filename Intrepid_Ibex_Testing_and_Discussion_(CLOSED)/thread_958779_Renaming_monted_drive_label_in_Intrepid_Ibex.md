---
title: "Renaming monted drive label in Intrepid Ibex"
date: 2008-10-25
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by toxik_ca on 2008-10-25
Hi everyone. This is my first post in here, and I hope you will find it useful. I installed Intrepid Ibex this afternoon. Everything went fine, except that drives' labels mounted in /media/ were all marked as "XX GB Media".

When I started nautilus using sudo, I could see the right labels (IE. /media/Archives was appearing as Archives in the left panel), but when I was using nautilus with lower access account the drives labels were still "XX GB Media".

After some research over google I managed to rename my drives' label in 5 steps (and I thought that sharing it would be useful):

1. Unmount the drive you want to change the label (if it is mounted)
```
sudo umount /dev/partitionId
```

2. Install e2label (if it is not already installed)
```
sudo apt-get install e2label
```

3. Rename this drive's label using e2label (repeat for other drives)
```
sudo e2label /dev/partitionId THENAMEYOUWANT
```

4. Restart Hardware abstraction layer hald
```
sudo /etc/init.d/hal restart
```

5. Mount your drive(s) manually or reboot (the drive label will appear correctly after rebooting if it is auto-mounted)
```
sudo mount -t ext3 /dev/partitionId /media/partitionId
```

I hope someone will find this little tutorial useful :)
Cheers

---

