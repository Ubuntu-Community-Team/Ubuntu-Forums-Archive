---
title: "Partitioning for boot speed"
date: 2009-04-02
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by SeanBlader on 2009-04-02
So it sounds like from what I've been able to find that we'll need a partition for /boot that's in Ext3. I'll want to do the other partitions in Ext4, but what would be the ideal sizes for setting said partitions on a 128gig SSD without using a swap partition in order to best allow for a best in class boot speed?

---

### Post by MacUntu on 2009-04-02
> **SeanBlader said:**
> So it sounds like from what I've been able to find that we'll need a partition for /boot that's in Ext3.
That's old news, one single EXT4 partition is enough (or two, if you prefer to have a separate home directory).

Don't know much about SSDs (yet), but you might wanna read this blog post by Ted Ts'o: [http://thunk.org/tytso/blog/2009/02/20/aligning-filesystems-to-an-ssds-erase-block-size/](http://thunk.org/tytso/blog/2009/02/20/aligning-filesystems-to-an-ssds-erase-block-size/)

---

### Post by SeanBlader on 2009-04-03
Well I've also heard it takes longer to mount a larger partition than it would a smaller one. In that case it would be at least a little more efficient to wait to mount /home until the system is waiting for the user to login. But there must be other boot speed strategies out there?

---

