---
title: "Migrating from latest evolution (with maildir) to Thunderbird"
date: 2011-10-27
forum: Installation &amp; Upgrades
---

### Post by Maximus86 on 2011-10-27
Hi All, 


I thought I'd write up a quick how-to for migrating from the latest Evolution to Thunderbird.

I upgraded from Ubuntu 11.04 to 11.11 on my work laptop, and after installation Evolution asked me to migrate my mailbox to a new format. I was planning to use Thunderbird later on, but decided to migrate my mailbox anyway.

This posed major problems when I finally decided to upgrade. Just copying over the folders to Thunderbird, as described in the majority of the how-to's you can find on line, did not work anymore because of the new format. 
Exporting my emails from Evolution to mbox generated HUGE mbox files (+60GB for ~1000 messages) that slowed down my pc to a grinding halt and caused numerous errors. I had to look for an alternative.

While the old Evolution used mbox, Evolution 3.2.0 uses the Maildir format, and stores individual mails as eml files. Without the extension. 


What I did was going in to ~.local/share/evolution/mail/local/cur (inbox folder with read mails) and run following script.
Replace [EXTENSION] with the actual current extension, my files looked like this:

> 1318609127.2526.bakske:2,S

Script:

```


#!/bin/bash

for i in *.[EXTENSION]*

do 
e=`echo $i | sed 's/.[EXTENSION]$/.eml/'`
cp $i $e
done


```

afterward I installed the import/export extension in Thunderbird, which let me import all eml files from a folder. 


If you have any info, tips or suggestions, shoot.

---

