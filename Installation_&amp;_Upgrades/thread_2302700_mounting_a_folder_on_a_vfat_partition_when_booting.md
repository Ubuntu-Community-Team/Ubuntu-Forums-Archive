---
title: "mounting a folder on a vfat partition when booting"
date: 2015-11-12
forum: Installation &amp; Upgrades
---

### Post by reut2 on 2015-11-12
I can mount the folder using:
> mount --bind /home/MyDocsOld/"My Documents" /home/reuven/"My Documents"
I recently added the following two lines to my /etc/fstab:
> UUID=CDC4-53E2                    /home/MyDocsOld    vfat    defaults,umask=007,gid=46 0       0
/home/MyDocsOld/"My Documents"    /home/reuven/"My Documents"    none    bind    

When I boot up I get a message that reads:
 > An error occured while mounting Documents".

Can someone tell me the correct fstab line to accomplish this please?

---

### Post by SeijiSensei on 2015-11-12
Try wrapping the whole pathname in quotes like this: "/home/reuven/My Documents" 

or use the backslash to "escape" the space like this:  /home/reuven/My\ Documents without any quotes.

---

### Post by reut2 on 2015-11-13
> **SeijiSensei said:**
> Try wrapping the whole pathname in quotes like this: "/home/reuven/My Documents" 

or use the backslash to "escape" the space like this:  /home/reuven/My\ Documents without any quotes.

After trying these suggestions and getting no success, I mounted the folder manually and copied the mtab line into the fstab file, and now it is working I'm not exactly understanding what the 040 is in there:
> /home/MyDocsOld/My\040Documents /home/reuven/My\040Documents none rw,bind 0 0

---

### Post by sisco311 on 2015-11-13
040 is the ASCII code of the space character in octal.

\ is the escape character and \040 is called an escape sequence.

Spaces and tabs have special meaning in the fstab file. They are used as field separators. 

In the shell (bash,dash...) you can use single and double quotes or the escape character (the backslash) to remove the special meaning of certain characters. But in the fstab file you are limited to use the \xxx escape sequence.

---

### Post by reut2 on 2015-11-13
Thank you!

---

