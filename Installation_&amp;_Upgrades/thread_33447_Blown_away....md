---
title: "Blown away..."
date: 2005-05-10
forum: Installation &amp; Upgrades
---

### Post by Mr Hatch on 2005-05-10
Hi,

I've just blown my Ubuntu-installation by mere stupidity I guess...

In the German Ubuntu-Community I asked for an easy and decent way to backup my system-partition, and before I could copy the whole text, the community went right into nirvana.

The suggestion is to boot into the live-environment, mount the root- and home-partitions and...

- to use gzip in order to...
save: sudo dd if=/dev/hdx | gzip -c > /mnt/home/ubuntu-root-$(date).img.gz
or
to restore the whole thing again:
sudo gunzip -c /mnt/home/ubuntu-root-$(date).image.gz | dd of=/dev/hdx

So far, so good, but BEFORE I should do that, I should erase any unimportant data from root by writing a zero-file and removing it again, so that compression could work at its best... just to have smaller backup-files.

And this exactly is the part I forgot to write down. I just did it out of memory and... you're guessing right... I zeroed the whole partition! *stop laughing plz

I really hope - as the German community will stay offline for quite a while I think - that somebody knows how I have to correctly write the zero-file without touching the existing data.

Thank you very much in advance.

---

### Post by tread on 2005-05-11
I don't understand .. what do you mean by zero file? If you want to create a file of size 0, you just say "touch new_file_name" .. but I am sure you don't mean that, do you?

---

### Post by Mr Hatch on 2005-05-11
[QUOTE=tread]I don't understand .. what do you mean by zero file? If you want to create a file of size 0, you just say "touch new_file_name" .. but I am sure you don't mean that, do you?[/QUOTE]

No, that's not what I mean.
I got advice to erase any "hidden" data on /dev/hdx before gzipping ist by overwriting it with a file containing zeroes. Let's say, Ubuntu-install is 2 GB on a 8 GB partition. When I booted into live-environment an gzipped the root-partition, it said that the gzip-file had a size of 3.8GB(!). I was told that gzip actually took formerly erased data with it, and that writing that "zero-file" into any area where no "real" data is to be found, makes the backup much smaller.
And in fact, the 3.8GB-file had about 600MB afterwards.
I'm simply looking for the right term how to tell ubuntu do exactly that: fill any area that doesn't contain real data with zeroes, so that I don't need a DVD-RW for any system-backup.

I think it's really hard to explain what this guy told me in German, but it's really clever to do by the way, and for me, it's a really comfortable way to backup my system on just a CD...

---

### Post by Juergen on 2005-05-11
If you mount your root-partition right under /mnt, just create a big file there:
```
dd if=/dev/zero of=/mnt/tmp/nulls
rm /mnt/tmp/nulls
```
You could also take a look at partimage, it ignores old data, so you don't need to overwrite your installation ;-)

---

