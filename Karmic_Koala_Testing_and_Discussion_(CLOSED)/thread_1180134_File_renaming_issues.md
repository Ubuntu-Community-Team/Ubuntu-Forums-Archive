---
title: "File renaming issues"
date: 2009-06-06
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by macroshaft on 2009-06-06
I'm not certain if this is a fault or not but when renaming a file which is all in capitals to exactly the same name but not capitals results in an error stating that a file with that name already exists.

I was certain linux is very case sensitive and so should be capable of having multiple files named the same with different combinations of caps and lower case.

---

### Post by slurdge on 2009-06-06
On what filesystem is this file ?
I'm not sure this would work with FAT for example.
Also, you can try this:
FILE1 => FILE2
FILE2 => file1

---

### Post by macroshaft on 2009-06-06
It's ext3, I've never had this issue before. I am renaming in that fashion already but that just makes things a bit more long winded.

---

### Post by afv on 2009-06-06
Working as expected, here (ext4).

---

### Post by meeples on 2009-06-07
i just had this an hour ago changing a folder on my mp3 player from "omgaudio" to "OMGAUDIO"... my mp3 is fat32

---

### Post by afv on 2009-06-07
> **meeples said:**
> i just had this an hour ago changing a folder on my mp3 player from "omgaudio" to "OMGAUDIO"... my mp3 is fat32

That's normal in FAT and NTFS…

---

### Post by macroshaft on 2009-06-07
It's just occured to me, my home partition is ext3 but my main external drive is FAT, I have mixed my locations up. Maybe I was renaming on my external drive at the time.

So problem probably solved.

---

