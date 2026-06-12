---
title: "Trouble saving torrent files to disk using Firefox"
date: 2006-12-05
forum: Installation &amp; Upgrades
---

### Post by CostasX2 on 2006-12-05
Hi,

I recently upgraded from 6.06 (Dapper Drake) to 6.10 (Edgy Eft). Everything was working perfectly until I tried to download a torrent file with Firefox 2.0.

Using the "Open with" option it works OK but when I try to save it using the "Save to Disk" option the torrent file is saved as "plain text document" file type with zero (0) file size. As you can imagine when I try to open that file with a torrent client I get an error due to empty content.

Prior to upgrade I was using Firefox 1.5 and I had no problems saving torrent files to the disk. This error does not appear when I try to download other types of files. I haven't test it with all possible file types but so far it only happens with torrents.

Any clue?

Thank you.

---

### Post by CostasX2 on 2006-12-09
Any idea?

---

### Post by raldz on 2006-12-13
Same here.. I could not download files.. it just downloads files with 0 bytes..

here is the error generated in the Error Console of Firefox..
```
Error: [Exception... "Component returned failure code: 0xc1f30001 (NS_ERROR_NOT_INITIALIZED) [nsIMIMEInfo.primaryExtension]"  nsresult: "0xc1f30001 (NS_ERROR_NOT_INITIALIZED)"  location: "JS frame :: file:///usr/lib/firefox/components/nsHelperAppDlg.js :: anonymous :: line 238"  data: no]
Source File: file:///usr/lib/firefox/components/nsHelperAppDlg.js
Line: 238
```

---

### Post by obi22 on 2007-01-15
The same here!

I was using FF2.0 without problems but afther upgrade to 2.0.0.1 it can't save files to destination other than default.

---

### Post by godfree2 on 2007-02-04
still no fix?!

---

### Post by godfree2 on 2007-02-04
disabling downthemall works for me

---

### Post by CostasX2 on 2007-02-07
> **godfree2 said:**
> disabling downthemall works for me
And how exactly do you do that?

---

### Post by Ambimom on 2007-02-07
Have you tried using Opera?  It has a built-in torrent client, but you can set it through opera:config to use any other client you wish.

---

### Post by webdr on 2007-02-07
This seems to be strictly a Firefox related problem.
I have chosen to run IE6 w/ WINE or OPERA to resolve this issue for now.
I have been researching the issue further and it seems that we may have to wait for FireFox to address this issue.
:)

---

### Post by confused57 on 2007-02-07
I think it's a Ubuntu repository Firefox problem...I'm running Dapper & installed Firefox 2.0.0.1, using this script:
[http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Install_Official_Mozilla_Build_of_Firefox](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Install_Official_Mozilla_Build_of_Firefox)

I just tried downloading the torrent file for Dapper alternate6.06.1 & the size was 27.5 kb...no problem downloading the file with Bittorrent(250 kb/sec)

Added: Not an Ubuntu repositories problem, I have Edgy on another partition with the default Firefox installation of 2.0.0.1...no problem downloading the alternate torrent iso, although it showed 27.4 kb, download started normally.

---

### Post by CostasX2 on 2007-02-07
> **Ambimom said:**
> Have you tried using Opera?  It has a built-in torrent client, but you can set it through opera:config to use any other client you wish.

 I've played around with Opera in the past, quite interesting browser, but I like Firefox too and I see no particular reason why I should switch to Opera.

---

### Post by CostasX2 on 2007-02-07
> **webdr said:**
> This seems to be strictly a Firefox related problem.
I have chosen to run IE6 w/ WINE or OPERA to resolve this issue for now.
I have been researching the issue further and it seems that we may have to wait for FireFox to address this issue.
:)

 No, this is not a Firefox specific problem.  I've tested a clean install of edgy eft in a virtual machine and Firefox works just fine, saving any number of torrents in the hard disk with no problem.  This is a dapper drake to edgy eft upgrade specific issue...

---

### Post by glotz on 2007-03-22
Seen these? (no solution yet)
[http://forums.mozillazine.org/viewtopic.php?t=531653](http://forums.mozillazine.org/viewtopic.php?t=531653)
[http://www.opensolaris.org/jive/thread.jspa?messageID=82502](http://www.opensolaris.org/jive/thread.jspa?messageID=82502)

---

### Post by CostasX2 on 2007-03-23
I wonder if this ever going to be fixed :mrgreen:

---

