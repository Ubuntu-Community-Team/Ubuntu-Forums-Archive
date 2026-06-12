---
title: "Duplicate app instances in file associations"
date: 2022-09-11
forum: Installation &amp; Upgrades
---

### Post by artist-wavenet on 2022-09-11
I have trouble opening LibreOffice files in Dolphin. When I right clock on a file I get two options for opening the file. One is the default LibreOffice writer instance that shows up right away. The second LibreOfficei Wrtier instance appears when I navigate to "Open With" as shown in the attached file: "Dolphin File Association two different writer apps.bmp". The default instances does not work. When I select it nothing happens. The second instance I must navigate to does work, and the file opens normally.

When I select "Other Application"  I see two instances of "LibreOffice", and "LibreOffice Writer", as shown in the attached file: "Dolphin File Association Duplicates.bmp". I attempted to solve this by removing all LibreOffice apps in Discover. I then used the apt command to also remove LibreOffice. The result was that the system no longer recognized the command "LibreOfficec" in the terminal emulator.

Then I installed LibreOffice with this command sequence:

```
sudo add-apt-repository ppa:libreoffice/ppa
sudo apt update 
sudo apt install libreoffice
```

This did not solve the problem of the two duplicates. I need this problem solved because I believe it related to the inability to open a LibreOffice document by simply pasting its path into Dolphin's filepath field. Why is this happening, and what is the solution?

The OS is Ubuntu Studio 22.04.1 on an encrypted, and RAIDed, ZFS file system.

---

