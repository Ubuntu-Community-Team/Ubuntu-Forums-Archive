---
title: "lilo configuration question"
date: 2008-11-23
forum: Installation &amp; Upgrades
---

### Post by 19bab79 on 2008-11-23
i have just dual booted my eee pc 900 ha. i am using lilo and am wondering if there is any way to change where my boot options show up on the screen. here is a link to the image that i am using:

[http://www.kde-look.org/content/show.php?content=11098&forumpage=4&PHPSESSID=cae](http://www.kde-look.org/content/show.php?content=11098&forumpage=4&PHPSESSID=cae)

my options show up above the first line of text (remember.... all i am offering). i want to make the options show up under "free your mind in:"

is there any way to configure where my boot options show up?

---

### Post by 19bab79 on 2008-11-24
i have figured out how to move the options around with the bmp-table option. i added the following line to my /etc/lilo.conf and experimented with the numbers until my boot options landed where i wanted:

bmp-table = 305p,365p,5,7

i have to admit, i am not sure what the 5 or 7 is for. the other two numbers are for the pixels. when i took the 5 and 7 out i got a warning that the bmp-table could spill of the screen. it didn't seem to make a difference though what value i put in those two positions, the options stayed in the same spot.

---

### Post by Sorivenul on 2008-11-24
> **19bab79 said:**
> i have to admit, i am not sure what the 5 or 7 is for. the other two numbers are for the pixels. when i took the 5 and 7 out i got a warning that the bmp-table could spill of the screen. it didn't seem to make a difference though what value i put in those two positions, the options stayed in the same spot.
A quick explanation of bmp-table in LILO:

**bmp-table=<x>,<y>,<ncol>,<nrow>,<xsep>,<spill>**
Specifies the location and layout of the menu table. <x> and <y> specify the starting x- and y-position of the upper left corner of the table in character coordinates: x in [1..80], y in [1..30]. <ncol> is the number of columns in the menu (1..5); and is the number of rows (entries) in each column. If more than one column is specified, then <xsep> is the number of character columns between the leftmost characters in each column: (18..40), and <spill> is the number of entries in one column which must be filled before entries spill into the next column. <spill> must be .le.<nrow>. If pixel addressing is used, instead of character addressing, then any of <x>,<y>, or <xsep> may be specified with a 'p' suffix on the decimal value.

From the LILO manpage.

---

