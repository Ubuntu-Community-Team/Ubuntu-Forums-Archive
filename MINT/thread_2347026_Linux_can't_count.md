---
title: "Linux can't count"
date: 2016-12-20
forum: MINT
---

### Post by Kevin McCready on 2016-12-20
I use vlc to play videos from a folder. The videos are numbered 1 to 999. They should play in that order. Instead, Linux plays file 1 then 100, then 101-109, then 10, then 110. Arggggahghhh!!! 

Is there a way to make Linux play nice?

DISTRIB_ID=LinuxMint
DISTRIB_RELEASE=18
DISTRIB_CODENAME=sarah
DISTRIB_DESCRIPTION="Linux Mint 18 Sarah"
NAME="Ubuntu"
VERSION="16.04 LTS (Xenial Xerus)"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu 16.04 LTS"
VERSION_ID="16.04"

---

### Post by SeijiSensei on 2016-12-20
Use three-digit numbers for every file, e.g., 001, 002, etc.

---

### Post by Kevin McCready on 2016-12-20
Ta for that, I'd rather not have to renumber the whole lot. I've heard there are two systems of counting, or more. Is there another way?

---

### Post by kpatz on 2016-12-20
There's two systems of "sorting"... one is alphanumeric (or more specifically, by character code) which is left-to-right and the other is numeric, right-to-left.

Since file names are alphanumeric, they are sorted alphanumerically (left to right), hence your file10 coming between file1 and file2.

Renaming the files with the same number of digits (so, file001, file002 etc.) would take care of the issue.

---

### Post by Keith_Helms on 2016-12-20
If you don't want to rename a bunch of files, you can just create a quick and dirty playlist with the files in the right order.  Change into the directory containing the files and run this.
```
ls -1 *.mkv | sort -n -k 3,3 > playlist.m3u
```

If you're not playing mkv files, change *.mkv to whatever suffix they have.

The -n option says do a numeric sort.

The -k 3,3 indicates what field the numeric key value is in.  If what you want to sort your titles on is in the first field, use 1,1.  If you want to sort on multiple fields, use something like 1,3.  

Then just open the playlist.m3u file instead of the videos.

---

### Post by Kevin McCready on 2016-12-20
Thanks Keith. That works! And thanks everyone. I've learnt some more!

---

