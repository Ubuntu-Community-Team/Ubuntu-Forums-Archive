---
title: "Partition + ATI drivers"
date: 2011-07-27
forum: Installation &amp; Upgrades
---

### Post by apostra on 2011-07-27
Hello guys,
for forum space saving I have 3 questions merged into one topic. Concerns my new system.

1)Partition: My old pc, got this set up, A: / , B: /home , C:/swap. Now I want to add an extra D:/ for data or anything other. I know how to make the 3 way partition, but the extra D:/ how do i label it, flag it? As another /home? Doesn't sound good idea for me. I want the D: partition to auto mount when I turn on pc.

2)I was searching web and saw some posts saying that, for virtual machines is good to have an extra partition, the posts I found was pretty old, thus I didn't keep them. Does that sound correct? Could you point me a guide that is accurate please?

3)ATI Drivers: I got 2 ATI 6870 for multi=gpu, I know, should be better if I choose nvidia. However, again, at google search I found many people referring to two types of ATI drivers, the open source and "the others". So my question is, which are the others? Catalyst are the open source or the others? If you got ATI drivers, which one play better on Ubuntu?

If already been asked on this forum apologize, please direct me to post.

Thanks in advance.

---

### Post by varunendra on 2011-07-28
1) Just create it, give it a meaningful name, create a mount point for it in your home folder or /media, and create an entry for it in /etc/fstab file, something like
```
/dev/sda4 /media/Data ext4 defaults 0 0
```
assuming that partition is seen as /dev/sda4 by Ubuntu, its file-system is ext4 and the preferred mount point (a directory) is created in /media whose name is "Data".
And by the way, most of the users don't get any extra advantage from a separate '/' partition AFAIK, so you may do away with it if you need so.

2) Keeping VMs on a separate partition makes them easier to manage. There is no performance gain unless this partition also lies on a separate 'drive', other than on which the host OS is installed.

3) Catalysts are proprietary ATI drivers. They are expected to give better performance. You should look into community documentation to see how good your card is supported. See:
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
[https://help.ubuntu.com/community/RadeonHD](https://help.ubuntu.com/community/RadeonHD)
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

If you need any help beyond this, I'd suggest to start a new corresponding thread for it and post a link to it here. 'Space' is not much of a problem. :)

 These forums are meant to be useful. So usability should be prime concern rather than 'space'. And separate threads for separate topics make them more useful - for you, for those who reply, and then for those who search them looking for solutions to their specific problems! :)

---

### Post by apostra on 2011-07-28
Thanks mate for your reply,

I did the normal way since there isn't much performance gain as you said.

For the drivers, I've got some issues, dunno if it is solved or not, I'm gonna post after I have a look at the links you provided.


Thanks again mate

---

### Post by marin123 on 2011-07-28
for ati drivers: you can install proprietary drivers from Additional drivers menu in Ubuntu, or by downloading them from here: [http://support.amd.com/us/gpudownload/Pages/index.aspx ]("http://support.amd.com/us/gpudownload/Pages/index.aspx")
I recommend installing from ati website because that drivers are newer.

open source drivers are good, but if you plan using any 3d app, you will need proprietary drivers...

---

