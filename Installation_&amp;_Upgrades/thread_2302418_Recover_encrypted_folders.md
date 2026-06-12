---
title: "Recover encrypted folders"
date: 2015-11-10
forum: Installation &amp; Upgrades
---

### Post by dyll131198 on 2015-11-10
Hi there
I had an installation of Ubuntu as of Saturday November 7 2015, this installation had been there since a couple months ago. In this installation I used cryptkeeper to encrypt a Folder callled "Dvaz'kzlye", this folder was mounted in /media/dyll131198/Storage/Data/Dvaz'kzlye/Dvaz'kzlye/.

On Sunday November 8 2015 I reinstalled Ubuntu, how can I get my encrypted folder (Dvaz'kzlye) back? Is it somewhere in the HDD called Storage?
And how can I decrypt my home folder from past installation?

Thanks in advance.

---

### Post by ajgreeny on 2015-11-10
Run command sudo parted -l to show us the partitions on your machine at the moment and it may be possible from its size or filesystem to figure out which is the Dvaz'kzlye partition, even if it was not labelled with that name.

I assume you do still know the passphrase for the encryption, as without that you will be unable to get anything back from that partition; that is the whole reason for using encryption in the first place.

---

### Post by dyll131198 on 2015-11-11
I've got a full system restore tarball, if that helps

First through console I entered Dvaz'kzlye dir and there are some folders named "." and "..", I guess my data is there.
[ATTACH=CONFIG]265598[/ATTACH]
Yes, I do still remember my passphrase.
Here's sudo parted -l output
[ATTACH=CONFIG]265599[/ATTACH]

---

### Post by howefield on 2015-11-11
Still a problem with your screenshot.

Try using the paperclip icon in the posting window (note: you won't see it in the quick reply window - you'll need to go advanced) to attach an image to our post, or if it is terminal output, it is much more readable if you copy/paste the output and post here between [code tags]("http://ubuntuforums.org/misc.php?do=bbcode").

---

### Post by dyll131198 on 2015-11-11
Here are the pictures
[ATTACH=CONFIG]265508[/ATTACH][ATTACH=CONFIG]265509[/ATTACH]

---

