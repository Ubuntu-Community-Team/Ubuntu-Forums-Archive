---
title: "md5sum does not work"
date: 2013-02-24
forum: Installation &amp; Upgrades
---

### Post by robinduncan on 2013-02-24
I have just downloaded the lubuntu12.10 iso and tried to check it.

Neither of the instructions for doing this here:

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

are giving me any joy.

automatic method gives me: command not found

semi-automatic method: I really can't work out what I'm supposed to download here, or how...

Any help much appreciated :D

---

### Post by ajgreeny on 2013-02-24
What OS are you using when you try to check the md5sum?
Have you tried the manual method in whatever OS you're using?

---

### Post by robinduncan on 2013-02-24
> **ajgreeny said:**
> What OS are you using when you try to check the md5sum?
Have you tried the manual method in whatever OS you're using?


Apologies, I meant to say I had tried the manual (not automatic) method, giving the above result.

I'm using ubuntu 11.04

Thanks for the reply

---

### Post by prodigy_ on 2013-02-24
Use attached script. Usage: ```
python cd-md5-verify.py /dev/cdrom /path/to/file.iso 
```

---

### Post by robinduncan on 2013-02-24
hi prodigy_

I get:

can't open file 'cd-md5-verify.py': [Errno 2] No such file or directory

But I have just seen that - I think - the fact that I downloaded the iso with transmission means that it was checked automatically. Does that sound right?

---

### Post by Gyokuro on 2013-02-24
Or you can type

openssl md5 downloaded.iso should do the same as md5sum which should be installed.

---

### Post by oldos2er on 2013-02-24
> **robinduncan said:**
> I'm using ubuntu 11.04


Just FYI, 11.04 is no longer supported, so you might want to upgrade.

---

### Post by robinduncan on 2013-02-24
> **Gyokuro said:**
> Or you can type

openssl md5 downloaded.iso should do the same as md5sum which should be installed.

That gives me:

downloaded.iso: No such file or directory

---

### Post by prodigy_ on 2013-02-24
> **robinduncan said:**
> can't open file 'cd-md5-verify.py': [Errno 2] No such file or directory
Sorry, I assumed you would run the script from the folder where you downloaded it. Anyway, try with full path:
```
python /path/to/cd-md5-verify.py /dev/cdrom /path/to/file.iso
```

---

### Post by robinduncan on 2013-02-24
I know 11.10 is no longer supported, but I was worried Ubuntu 12.04 would not work on my system. Someone recommended Lubuntu, and I'm trying to test-run it, but not getting very far.

I've just tried booting from the live dvd and choosing the check disk for errors option in the menu. It tells me that the kernel requires PAE, which I do not have. Would it be best to start again and download lubuntu 12.04?

---

### Post by robinduncan on 2013-02-24
thanks again prodigy_

I'm afraid you're dealing with a total illiterate.

With your second script I get:

python: can't open file '/path/to/cd-md5-verify.py': [Errno 2] No such file or directory

---

### Post by robinduncan on 2013-02-24
thanks again prodigy_

I'm afraid you're dealing with a total illiterate.

With your second script I get:

python: can't open file '/path/to/cd-md5-verify.py': [Errno 2] No such file or directory

---

### Post by prodigy_ on 2013-02-24
> **robinduncan said:**
> thanks again prodigy_

I'm afraid you're dealing with a total illiterate.

With your second script I get:

python: can't open file '/path/to/cd-md5-verify.py': [Errno 2] No such file or directory
**/path/to** is just a placeholder. :) You need to substitute it with actual path.

---

[Edit]: Just for fun - modified the script to look up in UbuntuHashes table.
```
#!/urs/bin/env python

import hashlib
import os
from sys import argv
import urllib2
import re

# http://www.joelverhagen.com/blog/2011/02/md5-hash-of-file-in-python/
def md5Checksum(file_path, file_size):
    with open(file_path, 'rb') as open_file:
        file_data = open_file.read(file_size)
        md5_checksum = hashlib.md5(file_data)
    return md5_checksum.hexdigest()

file_size = os.stat(argv[2]).st_size

for i in xrange(1,3):
    print md5Checksum(argv[i], file_size), argv[i]

hashes_url = "https://help.ubuntu.com/community/UbuntuHashes"

try:
    hashes_data = urllib2.urlopen(hashes_url).read()
    table_rows = hashes_data.split('</tr>')

    # Pattern for stripping HTML.
    re_pattern = re.compile(r'.*>[^\w]?([\w\.-]+).*', re.DOTALL)

    for table_row in table_rows:
        row_fields = table_row.split('</td>')
        row_fields[:] = [re.sub(re_pattern,
                                r'\1',
                                row_field) for row_field in row_fields]
        try:
            if row_fields[1] == argv[2]:
                print "\nFound in DB:", row_fields[0], row_fields[1]
                found = True
        except IndexError:
            pass

    try:
        found
    except NameError:
        print "\nNot found in DB!"
except:
    print "\nCould not read UbuntuHashes DB."
```

---

### Post by Gyokuro on 2013-02-24
> **robinduncan said:**
> That gives me:

downloaded.iso: No such file or directory

I have used downloaded.iso as an example as I do not know what you have downloaded. For example in case you have downloaded ubuntu-12.04.2-alternate-amd64.iso you will enter in your download directory where your ISO is:

openssl md5 ubuntu-12.04.2-alternate-amd64.iso

---

### Post by ajgreeny on 2013-02-25
> I've just tried booting from the live dvd and choosing the check disk  for errors option in the menu. It tells me that the kernel requires PAE,  which I do not have. Would it be best to start again and download  lubuntu 12.04?
Yes, I'm afraid that if your system can not use pae kernels you will have to go back to Lubuntu 12.04, (or I think Xubuntu 12.04 as well).

There are theoretical ways around this by editing the .iso file but for a computer illiterate, as you call yourself, it is not an option to go that route.  Lubuntu 12.04 is great, so you will still see most, if not all of what 12.10 can do.

PS:
> But I have just seen that - I think - the fact that I downloaded the iso  with transmission means that it was checked automatically. Does that  sound right?     To answer a query that nobody has yet responded to; yes, if you download the iso using transmission or other torrent client, it is checked and repaired if necessary as you download, so md5sum checks of the .iso are not strictly needed.

---

