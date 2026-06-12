---
title: "Copy Rhythmbox album covers to audio album dirs, helps Natty to Banshee"
date: 2011-05-21
forum: Installation &amp; Upgrades
---

### Post by chelala on 2011-05-21
Python script to copy all Album Covers from Rhythmbox to the audio director based on Rhythmbox XML database

It helped me use album covers in Banshee, as it shows jpg in the audio dir as album cover

don't know too much Python... change it, improve it, share it back

content of *covers2mp3dirs.py*

The script is based on my home dir */home/chelala* did not check function to guess profile dir

```
#!/usr/bin/python

import urllib
import os.path
import sys
from xml.etree.ElementTree import ElementTree
import shutil

doc = ElementTree(file='/home/chelala/.local/share/rhythmbox/rhythmdb.xml')

# entry type="song" location

for e in doc.findall(".//entry[@type='song']"):
    print '/home/chelala/.cache/rhythmbox/covers/' + e.find('./artist').text.encode('utf-8') + ' - ' + e.find('./album').text.encode('utf-8') + '.jpg'
    print os.path.dirname(urllib.unquote( e.find('./location').text ).replace("file://", ""))

    try:
        # Copy as found ARTIST - ALBUM.jpg
        shutil.copy('/home/chelala/.cache/rhythmbox/covers/' + e.find('./artist').text.encode('utf-8') + ' - ' + e.find('./album').text.encode('utf-8') + '.jpg', os.path.dirname(urllib.unquote( e.find('./location').text ).replace("file://", "")) )
        # Copy as Cover.jpg just in case
        shutil.copy('/home/chelala/.cache/rhythmbox/covers/' + e.find('./artist').text.encode('utf-8') + ' - ' + e.find('./album').text.encode('utf-8') + '.jpg', os.path.dirname(urllib.unquote( e.find('./location').text ).replace("file://", "")) + '/Cover.jpg' )
    except (IOError, os.error), why:
        print 'No jpg'
    print "========"

```

see you, Chelala

---

