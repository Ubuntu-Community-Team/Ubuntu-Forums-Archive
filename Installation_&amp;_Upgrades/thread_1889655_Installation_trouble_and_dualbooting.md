---
title: "Installation trouble and dualbooting"
date: 2011-12-01
forum: Installation &amp; Upgrades
---

### Post by mysteriousdarren on 2011-12-01
I recently was reinstalling Ubuntu 11.10 on my System 76 Serval Performance and was trying to dual-boot it with my Developer copy of Windows 8. I installed it along side each other or so I thought. I was going into update Ubuntu and add all my programs and drivers but ran into a problem. I can now access the other drive(NTFS), but I can only boot this drive(ext4). Is there anything I can do or is the only option reinstall the whole thing? Oh and another thing Ubuntu doesn’t boot up properly. It asks for what to boot then waits for what seems like forever with just the little waiting thing in the corner of the screen. Sometimes it boots but most of the time just sits there. It booted properly the first time, but only then.

---

### Post by oldfred on 2011-12-01
If you can boot or from liveCD run this:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.
Install these before running script:
sudo apt-get install mawk

---

