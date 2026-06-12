---
title: "PHP Fatal error:  Call to undefined function gzopen() in ... after upgrade"
date: 2014-04-18
forum: Installation &amp; Upgrades
---

### Post by Waldo_Nell on 2014-04-18
I have just upgraded from Ubuntu 12.04.4 LTS to 14.04.  Part of that was to upgrade Apache 2.2 to 2.4 and PHP5 to 5.2.9.

Since the upgrade I keep on getting gzopen() failures:

```

[FONT=Monaco]root@xxx:~ # cat file.php [/FONT]
[FONT=Monaco]<?php[/FONT]
[FONT=Monaco]
[/FONT]
[FONT=Monaco]$handle = gzopen('/tmp/main.gz','w9');[/FONT]
[FONT=Monaco]
[/FONT]
[FONT=Monaco]?>

[/FONT]
[FONT=Monaco]root@xxx:~ # php5 file.php 
[/FONT]
[FONT=Monaco]PHP Fatal error:  Call to undefined function gzopen() in /tmp/file.php on line 3

[/FONT]
[FONT=Monaco]root@xxx:~ # php5 -i | grep -i --color zlib[/FONT]
[FONT=Monaco]Registered PHP Streams => https, ftps, compress.zlib, compress.bzip2, php, file, glob, data, http, ftp, phar, zip[/FONT]
[FONT=Monaco]Registered Stream Filters => zlib.*, bzip2.*, convert.iconv.*, string.rot13, string.toupper, string.tolower, string.strip_tags, convert.*, consumed, dechunk[/FONT]
[FONT=Monaco]ZLib Version => 1.2.8[/FONT]
[FONT=Monaco]zlib[/FONT]
[FONT=Monaco]ZLib Support => enabled[/FONT]
[FONT=Monaco]Stream Wrapper => compress.zlib://[/FONT]
[FONT=Monaco]Stream Filter => zlib.inflate, zlib.deflate[/FONT]
[FONT=Monaco]zlib.output_compression => Off => Off[/FONT]
[FONT=Monaco]zlib.output_compression_level => -1 => -1[/FONT]
[FONT=Monaco]zlib.output_handler => no value => no value[/FONT]

```

---

### Post by Emeriz on 2014-04-19
I am getting the exact same errors when calling gzopen() and have not been able to find any way around it so far.

---

### Post by Waldo_Nell on 2014-04-19
Good to know I am not alone.  I have another machine that was on 13.10, which I also upgraded to 14.04, which has the same PHP version and that machine works.  I am at a loss.

---

### Post by Emeriz on 2014-04-19
Hmm, my machine was 12.10 ==> 13.10 and later from 13.10==>14.04 to get me to a LTS version.  I've thought about using a PPA to upgrade PHP to 5.5.11 or back to 5.4.  I'm just not sure that will work.  Re-installing php5-common did not help.

---

### Post by SeijiSensei on 2014-04-19
There are Launchpad reports for this bug in 2009 or so.  It apparently was fixed at that time.  In one of the postings in the bug report, this workaround was suggested: [https://bugs.launchpad.net/ubuntu/+source/php5/+bug/432291/comments/7](https://bugs.launchpad.net/ubuntu/+source/php5/+bug/432291/comments/7)

---

### Post by Emeriz on 2014-04-19
I'm not sure what workaround that thread gives, but perhaps I just missed it.  I did try to upgrade php to 5.5.11 via ppa:ondrej/php5 but I that fails due to unmet dependencies apparently. It seems that version is tied into apache and I am running nginx.

---

### Post by Waldo_Nell on 2014-04-19
If the workaround is to change code, I cannot do that - the code belongs to an external component and changing it would mean maintaining it throughout the life of the system.

---

### Post by Emeriz on 2014-04-19
I would prefer not to as well, but would as a short term solution.  Still looking for an alternative.

---

### Post by Emeriz on 2014-04-19
Okay, I was able to get stuff working again by changing the gzopen() reference to gzopen64() in my php files.  I'm still running some things so we'll see if this is an overall solution.

---

### Post by Waldo_Nell on 2014-04-19
That is interesting - that works for me too.  Wonder why gzopen() does not then just call gzopen64()...

---

