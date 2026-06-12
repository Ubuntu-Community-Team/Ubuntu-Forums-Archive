---
title: "Rhythmbox with foreign alphabets?"
date: 2006-09-28
forum: Installation &amp; Upgrades
---

### Post by Kauna on 2006-09-28
Hello,

I'm currently unable to view song titles that have e.g. scandinavians in their
file names. Is there a way to fix this?

---

### Post by Delkster on 2006-10-04
> **Kauna said:**
> Hello,

I'm currently unable to view song titles that have e.g. scandinavians in their
file names. Is there a way to fix this?

I wonder if those filenames are encoded using some other character set instead of UTF-8? As far as I know, Ubuntu uses UTF-8 for filename encoding and while Gnome applications seem generally decent at guessing if your filenames have actually been written using a different encoding (such as ISO-8859-1, also known as Latin-1), they may still cause some problems.

My filenames have been encoded in UTF-8 and work just fine with interesting characters in them (including Scandinavian ones) in Rhythmbox.

Do the names of your files appear correctly in Nautilus (the file manager)?

---

