---
title: "Help setting application preferences (MS Office 2007)"
date: 2009-03-27
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by richiewrt on 2009-03-27
Ok, I have managed to successfully installed Office 2007 under wine, but I can't figure out how to set word and excel as the default app for .doc and .xls files.  I am using Ubuntu 9.04 and the only place I see to set application preferences is System-->Preferences-->Prefered Applications but I don't see how to set it up for specific file extension. Thanks in advance for the help.

---

### Post by mikechant on 2009-03-27
I'm not at my Ubuntu PC at present, but I seem to remember if you right click on any doc or xls file and select properties, you can set a default application to open all files of that type.

---

### Post by BDNiner on 2009-03-27
Well you may have to use the command that launches the application. I don't quite remember but i think it goes something like
```

wine "/path to your office 07 application"

```
i think that you do need the quotes. but i don't have my pc in front of me so i can't say for sure.

---

### Post by richiewrt on 2009-03-27
> **mikechant said:**
> I'm not at my Ubuntu PC at present, but I seem to remember if you right click on any doc or xls file and select properties, you can set a default application to open all files of that type.


Thanks, this worked perfectly. I feel stupid for not seeing it before after spending so much time looking for it.

---

