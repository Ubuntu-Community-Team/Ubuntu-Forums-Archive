---
title: "ttf-mscorefonts-installer Installation Problem"
date: 2011-01-22
forum: Installation &amp; Upgrades
---

### Post by dehiker on 2011-01-22
I try to install wine on Ubuntu10.10 desktop, since I'm so willing to use Total Commander under linux. But I failed, and some problems come...

I have **"dpkg --purge"** the wine, but when right-clicking files, there're still four **"Wine core exe"** in the "open with", as shown in the first image. Do you know how to remove them?

Also, after the failure of wine installation, I always encounter **ttf-mscorefonts-installer** problem when I install or upgrade any package, as shown in other image. And I don't know how to terminate the report but to close the terminal! :cry:
Could you please give me any hints what was going wrong? And how can I install the **ttf-mscorefonts-installer** successfully?

Thank you so much for your attention!

dehiker

---

### Post by howefield on 2011-01-22
> **dehiker said:**
> And how can I install the **ttf-mscorefonts-installer** successfully?


Press the tab key to highlight the OK button, then the enter key, and you should be able to procede.

---

### Post by dehiker on 2011-01-22
Thank you so much, howefield!

Your prompt reply is of great help to me.

---

### Post by howefield on 2011-01-22
You're welcome, anytime.

I missed your first question about wine, try removing any wine-extension-*.desktop files in /home/user/.local/share/applications folder.

---

### Post by dehiker on 2011-01-22
Awesome! Thank you again, howefield!

---

