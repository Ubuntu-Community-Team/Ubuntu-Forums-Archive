---
title: "Gnome RDP error connecting to database - solve"
date: 2008-09-22
forum: Installation &amp; Upgrades
---

### Post by KarD_IO on 2008-09-22
After update from 7.10 to 8.04 gnome-rdp say "Gnome RDP error connecting to database". I solve problem this way:

.gnome-rdp.db - in sqllite 3 file format

1. in shell: sqlite3 /home/user/.gnome-rdp.db

sqlite> .output /home/user/RDP_3.sql
sqlite> .dump session version
sqlite> .exit

2. remove ./home/user/.gnome-rdp.db

3. sqlite /home/user/.gnome-rdp.db

sqlite> .read /home/user/RDP_3.sql
sqlite> .exit

that's all!

---

