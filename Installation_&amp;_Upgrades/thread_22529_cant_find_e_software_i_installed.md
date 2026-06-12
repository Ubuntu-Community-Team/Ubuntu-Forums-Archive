---
title: "cant find e software i installed"
date: 2005-03-28
forum: Installation &amp; Upgrades
---

### Post by kingofhell on 2005-03-28
i just installed AutoCad 2000 for my ubuntu by using wine. it was said to be at C:\ACAD2000 in the Autocad installation window but when i tried to cd C:\ACAD2000, my sys said that the directory is not invalid. so where is my autocad?

---

### Post by bored2k on 2005-03-28
[QUOTE=kingofhell]i just installed AutoCad 2000 for my ubuntu by using wine. it was said to be at C:\ACAD2000 in the Autocad installation window but when i tried to cd C:\ACAD2000, my sys said that the directory is not invalid. so where is my autocad?[/QUOTE]
 Wine created it in a fake windows environment , open your wine configuration and look for the fake environment directory, in my case for Crossover Office I would see something like ".cxoffice/fake_c" , but I am sure it is different.

---

