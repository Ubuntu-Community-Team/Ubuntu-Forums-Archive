---
title: "Problems tagging mp3 files in Rhythmbox"
date: 2010-04-07
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by rogerdean on 2010-04-07
Hello all

I've got a bit of an odd one here, and very frustrating. I have a large collection of mp3 files in Rhythmbox. Almost all are correctly tagged and organised, but a few just refuse to 'remember' their details.

I can edit the file properties in Rhythmbox (in this case for the genre) but 30 seconds or so later it reverts, presumably because RB is watching the folder and the change has not been successfully written.

I can correct the tags in EasyTag, and those changes seem to persist, but RB does not pick them up. I guess perhaps the two programs are looking for different versions of the ID3 tag?

I have looked into file permissions etc and think everything is as it should be. An example file that is causing me trouble is here -

[removed]

Anyone have any ideas? Cheers!
Roger


Edit - BTW I don't know that this is Lucid only, but that's what I'm using...

---

### Post by tekstr1der on 2010-04-07
Yep. I've run into this too. The files that are reverting after tagging with rhythmbox probably have APE tags. See:

Rhythmbox gives priority to APEv2 tags and won't display changes to ID3v2 tags
[https://bugs.launchpad.net/rhythmbox/+bug/235945](https://bugs.launchpad.net/rhythmbox/+bug/235945)

---

### Post by rogerdean on 2010-04-07
thanks very much, that put me on the right track. what a pain that this rhythmbox bug has been open for so long...

---

### Post by tekstr1der on 2010-04-07
FYI, you can use an alternative tag editing software to strip the APE tag from the files. I use mp3tag under win7. Once your files have only id3 tags, rhythmbox should handle everything as expected.

---

### Post by rogerdean on 2010-04-07
Yeah, that's what I ended up doing too. For the future though, is there any linux software that can do this?

---

### Post by TunaCanTommy on 2010-04-07
Look at Audio Tag Tool.  Use it to 'remove all tags' then retag with ID3v2.
Does batch tags very well, and you keep the file name in the ID3v2 tags.

---

### Post by rogerdean on 2010-04-07
thanks! i'll save that advice for the next time this comes up...

---

