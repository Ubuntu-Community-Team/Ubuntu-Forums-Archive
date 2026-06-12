---
title: "Ubuntu 7.0.4 w. mythTV cannot run mythtv-setup"
date: 2007-05-25
forum: Installation &amp; Upgrades
---

### Post by tuds47 on 2007-05-25
Hi
I have installed mythtv on a clean Ubuntu 7.0.4 desktop. But when I run the mythtv-setup, the Mythbackend must be close dialog is shown, an when I pres ok, some text is displayed (see beneath) and the session is killed (returns to the user login prompt).

What have I done wrong, or how do I troubleshoot the problem further?

Regards
Thorbjørn

```

Stopping MythTV server: mythbackend No /usr/bin/mythbackend found running; none killed.
.
2007-05-26 01:59:27.388 Using runtime prefix = /usr
2007-05-26 01:59:27.395 DPMS is active.
2007-05-26 01:59:27.416 New DB connection, total: 1
2007-05-26 01:59:27.446 Connected to database 'mythconverg' at host: localhost
2007-05-26 01:59:27.447 Total desktop dim: 800x600, with 1 screen[s].
2007-05-26 01:59:27.450 Using screen 0, 800x600 at 0,0
2007-05-26 01:59:27.459 Current Schema Version: 
2007-05-26 01:59:27.459 Newest Schema Version : 1160
2007-05-26 01:59:27.461 New DB connection, total: 2
2007-05-26 01:59:27.461 Connected to database 'mythconverg' at host: localhost
2007-05-26 01:59:27.480 Setting Lock for Database Schema upgrade. If you see a long pause here it means the Schema is already locked and is being upgraded by another Myth process.
2007-05-26 01:59:27.482 New DB connection, total: 3
2007-05-26 01:59:27.482 Connected to database 'mythconverg' at host: localhost
2007-05-26 01:59:27.483 Inserting MythTV initial database information.
2007-05-26 01:59:27.485 New DB connection, total: 4
2007-05-26 01:59:27.485 Connected to database 'mythconverg' at host: localhost
2007-05-26 01:59:27.485 Upgrading to schema version 1112
2007-05-26 01:59:27.748 New DB connection, total: 5
2007-05-26 01:59:27.748 Connected to database 'mythconverg' at host: localhost
2007-05-26 01:59:27.750 Upgrading to schema version 1113
2007-05-26 01:59:27.751 Upgrading to schema version 1114
2007-05-26 01:59:27.752 Upgrading to schema version 1115
2007-05-26 01:59:27.763 Upgrading to schema version 1116
2007-05-26 01:59:27.765 Upgrading to schema version 1117
2007-05-26 01:59:27.770 Upgrading to schema version 1118
2007-05-26 01:59:27.779 Upgrading to schema version 1119
2007-05-26 01:59:27.781 Upgrading to schema version 1120
2007-05-26 01:59:27.786 Upgrading to schema version 1121
2007-05-26 01:59:27.787 Upgrading to schema version 1122
2007-05-26 01:59:27.792 Upgrading to schema version 1123
2007-05-26 01:59:27.799 Upgrading to schema version 1124
2007-05-26 01:59:27.803 Upgrading to schema version 1125
2007-05-26 01:59:27.812 Upgrading to schema version 1126
2007-05-26 01:59:27.817 Upgrading to schema version 1127
2007-05-26 01:59:27.827 Upgrading to schema version 1128
2007-05-26 01:59:27.833 Upgrading to schema version 1129
2007-05-26 01:59:27.850 Upgrading to schema version 1130
2007-05-26 01:59:27.851 Upgrading to schema version 1131
2007-05-26 01:59:27.861 Upgrading to schema version 1132
2007-05-26 01:59:27.866 Upgrading to schema version 1133
2007-05-26 01:59:27.872 Upgrading to schema version 1134
2007-05-26 01:59:27.873 Upgrading to schema version 1135
2007-05-26 01:59:27.882 Upgrading to schema version 1136
2007-05-26 01:59:27.887 Upgrading to schema version 1137
2007-05-26 01:59:27.892 Upgrading to schema version 1138
2007-05-26 01:59:27.893 Upgrading to schema version 1139
2007-05-26 01:59:27.911 Upgrading to schema version 1140
2007-05-26 01:59:27.912 Upgrading to schema version 1141
2007-05-26 01:59:27.921 Upgrading to schema version 1142
2007-05-26 01:59:27.929 Upgrading to schema version 1143
2007-05-26 01:59:27.974 Upgrading to schema version 1144
2007-05-26 01:59:27.975 Upgrading to schema version 1145
2007-05-26 01:59:27.979 Upgrading to schema version 1146
2007-05-26 01:59:27.980 Upgrading to schema version 1147
2007-05-26 01:59:28.035 Upgrading to schema version 1148
2007-05-26 01:59:28.109 Upgrading to schema version 1149
2007-05-26 01:59:28.112 Upgrading to schema version 1150
2007-05-26 01:59:28.113 Upgrading to schema version 1151
2007-05-26 01:59:28.126 Upgrading to schema version 1152
2007-05-26 01:59:28.131 Upgrading to schema version 1153
2007-05-26 01:59:28.140 Upgrading to schema version 1154
2007-05-26 01:59:28.150 Upgrading to schema version 1155
2007-05-26 01:59:28.158 Upgrading to schema version 1156
2007-05-26 01:59:28.163 Upgrading to schema version 1157
2007-05-26 01:59:28.164 Upgrading to schema version 1158
2007-05-26 01:59:28.180 Upgrading to schema version 1159
2007-05-26 01:59:28.186 Upgrading to schema version 1160
2007-05-26 01:59:28.187 Database Schema upgrade complete, unlocking.
2007-05-26 01:59:28.203 Total desktop dim: 800x600, with 1 screen[s].
2007-05-26 01:59:28.204 Using screen 0, 800x600 at 0,0
2007-05-26 01:59:28.206 Switching to square mode (G.A.N.T.)
2007-05-26 01:59:28.245 Using the Qt painter

```

---

