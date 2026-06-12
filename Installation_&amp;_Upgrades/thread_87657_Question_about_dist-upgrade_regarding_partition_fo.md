---
title: "Question about dist-upgrade regarding partition formatting"
date: 2005-11-08
forum: Installation &amp; Upgrades
---

### Post by netox on 2005-11-08
My question is:  if I do a dist-upgrade via apt-get, will I have the option to change the partition from ext2 to ext3, journalized?
I know it sounds improbable, but I just wanna make sure, because if not I'll do a clean install.

---

### Post by manicka on 2005-11-08
No you won't

---

### Post by matthew on 2005-11-08
It is possible (and not especially difficult) to convert an existing ext2 filesystem to ext3 by adding a journal. Here's how.

Say your filesystem is on /dev/hda4

First unmount it (actually, I'm not 100% sure this is necessary, but it seems like a really good idea)
```
sudo umount /dev/hda4
``` then convert it
```
sudo tune2fs -j /dev/hda4
``` then remount
```
sudo mount /dev/hda4
``` Then edit the entry in /etc/fstab for that partition to read "ext3" where it currently reads "ext2"

That's it. See the man page for tune2fs for more details.

---

### Post by manicka on 2005-11-09
[QUOTE=matthew]It is possible (and not especially difficult) to convert an existing ext2 filesystem to ext3 by adding a journal. Here's how.
[/QUOTE]
But can you do that with the active / partition? which is what I think netox wants to do

Maybe with a knoppix cd?

---

### Post by netox on 2005-11-09
[QUOTE=manicka]But can you do that with the active / partition? which is what I think netox wants to do

Maybe with a knoppix cd?[/QUOTE]

Thanks for your replies guys.
Yeah, that's what kinda complicated things for me.  How can I unmount the active partition?

---

### Post by matthew on 2005-11-09
[quote=netox]Thanks for your replies guys.
Yeah, that's what kinda complicated things for me. How can I unmount the active partition?[/quote] I'm not sure you can. Sorry, I wasn't thinking--thanks, manicka for helping me wake up a bit.

What you can do is use a cd-based linux distro like the Ubuntu live cd or Knoppix that will allow you to run an operating system without having a hard drive mounted. Then you can do what I mentioned before. Sorry about the confusion.

You could try to do this with the partition mounted. I read the man page for tune2fs and I didn't see where it is necessary for the partition to be unmounted so it may work. It also says
> -j     Add  an ext3 journal to the filesystem.  If the -J option is not
              specified, the default journal parameters will be used to create
              an  appropriately  sized journal (given the size of the filesys&#8208;
              tem) stored within the filesystem.  Note that you must be  using
              a kernel which has ext3 support in order to actually make use of
              the journal.

 If this option is used to create a journal on a mounted filesys&#8208;
              tem,  an  immutable  file, .journal, will be created in the top-
              level directory of the filesystem, as it is the only safe way to
              create the journal inode while the filesystem is mounted. The standard warning applies here: **make sure you have a good backup** first just in case!

---

