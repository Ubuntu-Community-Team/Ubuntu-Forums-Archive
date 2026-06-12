---
title: "Plain quote and double-quote in gedit?"
date: 2007-10-22
forum: Installation &amp; Upgrades
---

### Post by Unterseeboot_234 on 2007-10-22
Hello,

Just upgraded to Gutsy Gibbon, 7.10, desktop 64-bit. I like it. The only issue thus far is gEdit has ¨sticky¨ quote and double-quote marks on the keyboard. Not good. I would expect that feature in a word-processor, but not an editor. I want the regular single-character quote and single-character quote marks for Python code. The quotes I need don´t angle. Is there a way to set an option on gEdit????

Thanks.

==============

Played around with gEdit => Application => Accessories => Text Editor. Which used to be just fine for code work in java or Python. Now gEdit adds hidden UTF-8 characters throughout the file. To code Python now takes:

```

# -*- coding: iso-8859-1 -*-

'''
This is a test of python.
-->>>>> [single-quote + spacebar] gives UTF-16: 0x0027
'''

for i in range(5):
	print '&#314;ine %d' % i
 
```

============

On the install:  I selected English_international for the keyboard. After using Gibbon for a day, I found System==> Preferences ==> Keyboard ==> added English keyboard w/ option "make default". Reboot. And now I've got signle and double quote marks as they should be. Which is great. I really like Gibbon. The English_international made my web pages show pages with all characters. I'm happy to have a plain text editor back again.

---

