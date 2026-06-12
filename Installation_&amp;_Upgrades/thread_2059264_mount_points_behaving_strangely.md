---
title: "mount points behaving strangely"
date: 2012-09-17
forum: Installation &amp; Upgrades
---

### Post by s_raghu20 on 2012-09-17
Hi,

Its bizzare, so I dont know how to put it the right way.. I'd just say it as it happens...

1. Start any app (e.g. Rhythmbox, virtualbox etc). 
2. To start with, your stored configurations (e.g. imported music, or virtual hard disks) will be reported as missing...  
3. Now, I try to add them again (every time.. believe me its frustrating). Open the dialog box, and as soon as the folder "music" is chosen, the app (fhythmbox in this case) is able to find all files just like that.. I just cancel the import dialog and all is well...

Virtual box behaves even more funny.. I open the choose virtual hard disk dialog, and it lets me select a vhd file. when I click on "open", the application (virtualbox) crashes. Gone. foo.

When I restart the application again, all is well..


Is something going crazy with my disk structures ?

I have 3 internal hdds, 250, 500 GB and a 2TB one. all of them are in automount mode through fstab.. nothing special configured either way.

this has started happening since about a month or so back..

help..

---

### Post by darkod on 2012-09-17
Are you sure the automount is done correctly? It sounds like it's not. That's why after you click the partition/folder once, it works from there on because by clicking it is mounting it.

Did you use the UUIDs in fstab or /dev/sdXY? Because the order of your disks might have changed and the /dev/sdXY not to be correct any more.

---

