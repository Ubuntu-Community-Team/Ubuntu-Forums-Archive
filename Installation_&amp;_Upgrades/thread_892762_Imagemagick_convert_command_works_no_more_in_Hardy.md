---
title: "Imagemagick convert command works no more in Hardy 8.04"
date: 2008-08-17
forum: Installation &amp; Upgrades
---

### Post by ozanmert on 2008-08-17
Hi All,

I had been using the convert command of Imagemagick for years without a problem, to convert postscript files to jpg, png etc. on various Debian and Ubuntu distributions.... until yesterday, when I did an upgrade from Gutsy to Hardy.

"convert" command now fails with the following error messages. "humid.ps" exists.

```
$convert -density 100x100 humid.ps humid.png

convert: Postscript delegate failed `humid.ps': No such file or directory.
convert: missing an image filename `humid.png'
```

or with the following, depending on the specific postscript file:

```
$convert -density 100x100 cells.ps cells.png

Error: /dictstackunderflow in --end--
Operand stack:

Execution stack:
   %interp_exit   .runexec2   --nostringval--   --nostringval--   --nostringval--   2   %stopped_push   --nostringval--   --nostringval--   --nostringval--   false   1   %stopped_push   1905   1   3   %oparray_pop   1904   1   3   %oparray_pop   1888   1   3   %oparray_pop   1771   1   3   %oparray_pop   --nostringval--   %errorexec_pop   .runexec2   --nostringval--   --nostringval--   --nostringval--   2   %stopped_push   --nostringval--
Dictionary stack:
   --dict:1156/1684(ro)(G)--   --dict:0/20(G)--   --dict:94/200(L)--
Current allocation mode is local
Current file position is 8629
GPL Ghostscript 8.61: Unrecoverable error, exit code 1
Error: /dictstackunderflow in --end--
Operand stack:

Execution stack:
   %interp_exit   .runexec2   --nostringval--   --nostringval--   --nostringval--   2   %stopped_push   --nostringval--   --nostringval--   --nostringval--   false   1   %stopped_push   1905   1   3   %oparray_pop   1904   1   3   %oparray_pop   1888   1   3   %oparray_pop   1771   1   3   %oparray_pop   --nostringval--   %errorexec_pop   .runexec2   --nostringval--   --nostringval--   --nostringval--   2   %stopped_push   --nostringval--
Dictionary stack:
   --dict:1156/1684(ro)(G)--   --dict:0/20(G)--   --dict:94/200(L)--
Current allocation mode is local
Current file position is 8629
GPL Ghostscript 8.61: Unrecoverable error, exit code 1
convert: Postscript delegate failed `cells.ps': No such file or directory.
convert: missing an image filename `cells.png'.
```

I digged Google to no luck. Some say this is a Ghostscript problem. I have the Ghostscript version 8.61, Imagemagick 6.4.2.

Please help me solve this very annoying problem. I don't understand why the developers ruin this kind of very fundamental thing.

Thanks in advance

---

### Post by cariboo on 2008-08-17
The message you are getting is stating that it can't find the .ps files. Have you tried using the path to the file eg:

```
/home/usr/filename.ps
```

Jim

---

### Post by ozanmert on 2008-08-17
> **cariboo907 said:**
> The message you are getting is stating that it can't find the .ps files. Have you tried using the path to the file eg:

```
/home/usr/filename.ps
```

Jim

Thanks Jim, but as I wrote:

***"humid.ps" exists***

---

### Post by ozanmert on 2008-08-17
FOR EVERYONE'S INFORMATION

After searching hours and hours for a solution, I solved my own problem by removing the apt version of Imagemagick and manually installing an older version. It is the version 6.2.8. As I read in another forum, versions starting from 6.3 have the potential of not being able to work with Ghostscript properly. The reason is unknown.

It is hard to conceive how the developers manage to ruin the stability of a software of this importance. I want to remind them here, on behalf of everyone that the primary philosophy of GNU is to provide free and useful software to the public, and **NOT** to create new versions every other day and advertise them at the expense of hard-earned stability.

---

### Post by daltonh on 2008-12-18
I was getting an error (convert: Postscript delegate failed) trying to convert an eps file to a jpg using convert (imagemagick) in hardy.  Following this thread I tried a few things, including installing GPL gs from source (8.63) but the error remained.

Then noticed an ubuntu package graphicsmagick-imagemagick-compat which replaces imagemagick with apparently similar functionality.  Installed that and the problem was solved.

Hope this helps someone.

---

### Post by Luffield on 2009-03-04
> **daltonh said:**
> Then noticed an ubuntu package graphicsmagick-imagemagick-compat which replaces imagemagick with apparently similar functionality.  Installed that and the problem was solved.

Hope this helps someone.

It did - thanks!

---

