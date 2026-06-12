---
title: "dpkg problems - newb"
date: 2008-03-01
forum: Installation &amp; Upgrades
---

### Post by elmick on 2008-03-01
Hi,

This is my first post.

Ive got problems with these packages:
$dpkg --audit:
```

The following packages are in a mess due to serious problems during
installation.  They must be reinstalled for them (and any packages
that depend on them) to function properly:
 metacity-common      Shared files of lightweight GTK2 based Window Manager

The following packages have been unpacked but not yet configured.
They must be configured using dpkg --configure or the configure
menu option in dselect for them to work:
 metacity             A lightweight GTK2 based Window Manager
 gnome-panel          launcher and docking facility for GNOME 2
 gnome-control-center utilities to configure the GNOME desktop
 libmetacity0         library of lightweight GTK2 based Window Manager

The following packages are only half configured, probably due to problems
configuring them the first time.  The configuration should be retried using
dpkg --configure <package> or the configure menu option in dselect:
 desktop-base         common files for the Debian Desktop
 gnome-panel-data     common files for GNOME 2 panel

```

When I try to configure (dpkg --configure -a) or try to install metacity-common I get lots of errors of the form:
   /tmp/gconf-xxxxx/temp.entries: xxx: parser error : <error>

for example:
```

Setting up desktop-base (4.0.0) ...
/tmp/gconf-w95UDB/temp.entries:107 parser error : Opening and ending tag mismatch:
 line 107 and key
y><schema_key>/schemas/apps/panel/objects/attached_toplevel_id</schema_key></key

...
...
...

dpkg: error processing desktop-base (--configure)
...
...

```

i cant start terminal and cant figure out how to copy from Xterm so had to type it out.

Can anyone help?

---

### Post by PmDematagoda on 2008-03-01
Post the outputs of:-
```
sudo dpkg --configure -a
```
and
```
sudo apt-get install -f
```

---

### Post by elmick on 2008-03-01
i cant start terminal and cant figure out how to copy from Xterm? Its too long to type out.

i tried sudo dpkg --configure -a > confg.txt but that somehow only got the first two lines.

---

### Post by elmick on 2008-03-01
> **PmDematagoda said:**
> 
```
sudo apt-get install -f
```

gave similar parser errors but piping it to a txt file only gave the first few lines :

```

Reading package lists...
Building dependency tree...
Reading state information...
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
7 not fully installed or removed.
Need to get 0B/471kB of archives.
After unpacking 0B of additional disk space will be used.
(Reading database ... 94148 files and directories currently installed.)
Preparing to replace metacity-common 1:2.18.2-0ubuntu1 (using .../metacity-common_1%3a2.18.2-0ubuntu1_all.deb) ...
Unpacking replacement metacity-common ...

```

---

### Post by elmick on 2008-03-01
got a mouse with middle button. here is output of --configure:

```

mick@mick-laptop:~$ sudo dpkg --configure -a
Setting up desktop-base (4.0.0) ...
/tmp/gconf-ijTRcF/temp.entries:107: parser error : Opening and ending tag mismat
ch: entry line 107 and key
y><schema_key>/schemas/apps/panel/objects/attached_toplevel_id</schema_key></key
                                                                               ^
/tmp/gconf-ijTRcF/temp.entries:111: parser error : Opening and ending tag mismat
ch: key line 107 and entry
</entry>
        ^
/tmp/gconf-ijTRcF/temp.entries:113: parser error : error parsing attribute name
<key><entrylist</key>
               ^
/tmp/gconf-ijTRcF/temp.entries:113: parser error : attributes construct error
<key><entrylist</key>
               ^
/tmp/gconf-ijTRcF/temp.entries:113: parser error : Couldn't find end of Start Ta
g entrylist line 113
<key><entrylist</key>
               ^
/tmp/gconf-ijTRcF/temp.entries:125: parser error : Opening and ending tag mismat
ch: entry line 125 and key
y><schema_key>/schemas/apps/panel/objects/attached_toplevel_id</schema_key></key
                                                                               ^
/tmp/gconf-ijTRcF/temp.entries:129: parser error : Opening and ending tag mismat
ch: key line 125 and entry
</entry>
        ^
/tmp/gconf-ijTRcF/temp.entries:137: parser error : Opening and ending tag mismat
ch: entry line 137 and key
y><schema_key>/schemas/apps/panel/objects/attached_toplevel_id</schema_key></key
                                                                               ^
/tmp/gconf-ijTRcF/temp.entries:141: parser error : Opening and ending tag mismat
ch: key line 137 and entry
</entry>
        ^
/tmp/gconf-ijTRcF/temp.entries:143: parser error : Opening and ending tag mismat
ch: entry line 143 and key
y><schema_key>/schemas/apps/panel/objects/attached_toplevel_id</schema_key></key
                                                                               ^
/tmp/gconf-ijTRcF/temp.entries:147: parser error : Opening and ending tag mismat
ch: key line 143 and entry
</entry>
        ^
/tmp/gconf-ijTRcF/temp.entries:161: parser error : Opening and ending tag mismat
ch: entry line 161 and key
y><schema_key>/schemas/apps/panel/objects/attached_toplevel_id</schema_key></key
                                                                               ^
/tmp/gconf-ijTRcF/temp.entries:165: parser error : Opening and ending tag mismat
ch: key line 161 and entry
</entry>
        ^
/tmp/gconf-ijTRcF/temp.entries:179: parser error : Opening and ending tag mismat
ch: entry line 179 and key
y><schema_key>/schemas/apps/panel/objects/attached_toplevel_id</schema_key></key
                                                                               ^
/tmp/gconf-ijTRcF/temp.entries:183: parser error : Opening and ending tag mismat
ch: key line 179 and entry
</entry>
        ^
/tmp/gconf-ijTRcF/temp.entries:197: parser error : Opening and ending tag mismat
ch: entry line 197 and key
y><schema_key>/schemas/apps/panel/objects/attached_toplevel_id</schema_key></key
                                                                               ^
/tmp/gconf-ijTRcF/temp.entries:201: parser error : Opening and ending tag mismat
ch: key line 197 and entry
</entry>
        ^
/tmp/gconf-ijTRcF/temp.entries:209: parser error : error parsing attribute name
<key><list</key>
          ^
/tmp/gconf-ijTRcF/temp.entries:209: parser error : attributes construct error
<key><list</key>
          ^
/tmp/gconf-ijTRcF/temp.entries:209: parser error : Couldn't find end of Start Ta
g list line 209
<key><list</key>
          ^
/tmp/gconf-ijTRcF/temp.entries:215: parser error : Opening and ending tag mismat
ch: entry line 215 and key
y><schema_key>/schemas/apps/panel/objects/attached_toplevel_id</schema_key></key
                                                                               ^
/tmp/gconf-ijTRcF/temp.entries:219: parser error : Opening and ending tag mismat
ch: key line 215 and entry
</entry>
        ^
/tmp/gconf-ijTRcF/temp.entries:227: parser error : Opening and ending tag mismat
ch: entry line 227 and key
y><schema_key>/schemas/apps/panel/objects/attached_toplevel_id</schema_key></key
                                                                               ^
/tmp/gconf-ijTRcF/temp.entries:231: parser error : Opening and ending tag mismat
ch: key line 227 and entry
</entry>
        ^
/tmp/gconf-ijTRcF/temp.entries:267: parser error : Comment not terminated 
<!--</key>
<value>
  <string>TrashApplet Applet 
  <string>TrashApplet Applet --&gt;</string>
                             ^
/tmp/gconf-ijTRcF/temp.entries:356: parser error : Comment not terminated

^
/tmp/gconf-ijTRcF/temp.entries:356: parser error : Premature end of data in tag 
key line 265

^
/tmp/gconf-ijTRcF/temp.entries:356: parser error : Premature end of data in tag 
entry line 264

^
/tmp/gconf-ijTRcF/temp.entries:356: parser error : Premature end of data in tag 
entry line 226

^
/tmp/gconf-ijTRcF/temp.entries:356: parser error : Premature end of data in tag 
entry line 214

^
/tmp/gconf-ijTRcF/temp.entries:356: parser error : Premature end of data in tag 
entry line 196

^
/tmp/gconf-ijTRcF/temp.entries:356: parser error : Premature end of data in tag 
entry line 178

^
/tmp/gconf-ijTRcF/temp.entries:356: parser error : Premature end of data in tag 
entry line 160

^
/tmp/gconf-ijTRcF/temp.entries:356: parser error : Premature end of data in tag 
entry line 142

^
/tmp/gconf-ijTRcF/temp.entries:356: parser error : Premature end of data in tag 
entry line 136

^
/tmp/gconf-ijTRcF/temp.entries:356: parser error : Premature end of data in tag 
entry line 124

^
/tmp/gconf-ijTRcF/temp.entries:356: parser error : Premature end of data in tag 
entry line 106

^
/tmp/gconf-ijTRcF/temp.entries:356: parser error : Premature end of data in tag 
entrylist line 2

^
/tmp/gconf-ijTRcF/temp.entries:356: parser error : Premature end of data in tag 
gconfentryfile line 1

^
dpkg: error processing desktop-base (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of metacity:
 metacity depends on metacity-common (>= 1:2.18); however:
  Package metacity-common is not installed.
 metacity depends on metacity-common (<< 1:2.19); however:
  Package metacity-common is not installed.
dpkg: error processing metacity (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libmetacity0:
 libmetacity0 depends on metacity-common (>= 1:2.18); however:
  Package metacity-common is not installed.
 libmetacity0 depends on metacity-common (<< 1:2.19); however:
  Package metacity-common is not installed.
dpkg: error processing libmetacity0 (--configure):
 dependency problems - leaving unconfigured
Setting up gnome-panel-data (2.18.1-0ubuntu3.1) ...
laptop configuration
/tmp/gconf-etvrge/temp.entries:107: parser error : Opening and ending tag mismatch: entry line 107 and key
y><schema_key>/schemas/apps/panel/objects/attached_toplevel_id</schema_key></key
                                                                               ^
/tmp/gconf-etvrge/temp.entries:111: parser error : Opening and ending tag mismatch: key line 107 and entry
</entry>
        ^
/tmp/gconf-etvrge/temp.entries:113: parser error : error parsing attribute name
<key><entrylist</key>
               ^
/tmp/gconf-etvrge/temp.entries:113: parser error : attributes construct error
<key><entrylist</key>
               ^
/tmp/gconf-etvrge/temp.entries:113: parser error : Couldn't find end of Start Tag entrylist line 113
<key><entrylist</key>
               ^
/tmp/gconf-etvrge/temp.entries:125: parser error : Opening and ending tag mismatch: entry line 125 and key
y><schema_key>/schemas/apps/panel/objects/attached_toplevel_id</schema_key></key
                                                                               ^
/tmp/gconf-etvrge/temp.entries:129: parser error : Opening and ending tag mismatch: key line 125 and entry
</entry>
        ^
/tmp/gconf-etvrge/temp.entries:137: parser error : Opening and ending tag mismatch: entry line 137 and key
y><schema_key>/schemas/apps/panel/objects/attached_toplevel_id</schema_key></key
                                                                               ^
/tmp/gconf-etvrge/temp.entries:141: parser error : Opening and ending tag mismatch: key line 137 and entry
</entry>
        ^
/tmp/gconf-etvrge/temp.entries:143: parser error : Opening and ending tag mismatch: entry line 143 and key
y><schema_key>/schemas/apps/panel/objects/attached_toplevel_id</schema_key></key
                                                                               ^
/tmp/gconf-etvrge/temp.entries:147: parser error : Opening and ending tag mismatch: key line 143 and entry
</entry>
        ^
/tmp/gconf-etvrge/temp.entries:161: parser error : Opening and ending tag mismatch: entry line 161 and key
y><schema_key>/schemas/apps/panel/objects/attached_toplevel_id</schema_key></key
                                                                               ^
/tmp/gconf-etvrge/temp.entries:165: parser error : Opening and ending tag mismatch: key line 161 and entry
</entry>
        ^
/tmp/gconf-etvrge/temp.entries:179: parser error : Opening and ending tag mismatch: entry line 179 and key
y><schema_key>/schemas/apps/panel/objects/attached_toplevel_id</schema_key></key
                                                                               ^
/tmp/gconf-etvrge/temp.entries:183: parser error : Opening and ending tag mismatch: key line 179 and entry
</entry>
        ^
/tmp/gconf-etvrge/temp.entries:197: parser error : Opening and ending tag mismatch: entry line 197 and key
y><schema_key>/schemas/apps/panel/objects/attached_toplevel_id</schema_key></key
                                                                               ^
/tmp/gconf-etvrge/temp.entries:201: parser error : Opening and ending tag mismatch: key line 197 and entry
</entry>
        ^
/tmp/gconf-etvrge/temp.entries:209: parser error : error parsing attribute name
<key><list</key>
          ^
/tmp/gconf-etvrge/temp.entries:209: parser error : attributes construct error
<key><list</key>
          ^
/tmp/gconf-etvrge/temp.entries:209: parser error : Couldn't find end of Start Tag list line 209
<key><list</key>
          ^
/tmp/gconf-etvrge/temp.entries:215: parser error : Opening and ending tag mismatch: entry line 215 and key
y><schema_key>/schemas/apps/panel/objects/attached_toplevel_id</schema_key></key
                                                                               ^
/tmp/gconf-etvrge/temp.entries:219: parser error : Opening and ending tag mismatch: key line 215 and entry
</entry>
        ^
/tmp/gconf-etvrge/temp.entries:227: parser error : Opening and ending tag mismatch: entry line 227 and key
y><schema_key>/schemas/apps/panel/objects/attached_toplevel_id</schema_key></key
                                                                               ^
/tmp/gconf-etvrge/temp.entries:231: parser error : Opening and ending tag mismatch: key line 227 and entry
</entry>
        ^
/tmp/gconf-etvrge/temp.entries:267: parser error : Comment not terminated 
<!--</key>
<value>
  <string>TrashApplet Applet 
  <string>TrashApplet Applet --&gt;</string>
                             ^
/tmp/gconf-etvrge/temp.entries:356: parser error : Comment not terminated

^
/tmp/gconf-etvrge/temp.entries:356: parser error : Premature end of data in tag key line 265

^
/tmp/gconf-etvrge/temp.entries:356: parser error : Premature end of data in tag entry line 264

^
/tmp/gconf-etvrge/temp.entries:356: parser error : Premature end of data in tag entry line 226

^
/tmp/gconf-etvrge/temp.entries:356: parser error : Premature end of data in tag entry line 214

^
/tmp/gconf-etvrge/temp.entries:356: parser error : Premature end of data in tag entry line 196

^
/tmp/gconf-etvrge/temp.entries:356: parser error : Premature end of data in tag entry line 178

^
/tmp/gconf-etvrge/temp.entries:356: parser error : Premature end of data in tag entry line 160

^
/tmp/gconf-etvrge/temp.entries:356: parser error : Premature end of data in tag entry line 142

^
/tmp/gconf-etvrge/temp.entries:356: parser error : Premature end of data in tag entry line 136

^
/tmp/gconf-etvrge/temp.entries:356: parser error : Premature end of data in tag entry line 124

^
/tmp/gconf-etvrge/temp.entries:356: parser error : Premature end of data in tag entry line 106

^
/tmp/gconf-etvrge/temp.entries:356: parser error : Premature end of data in tag entrylist line 2

^
/tmp/gconf-etvrge/temp.entries:356: parser error : Premature end of data in tag gconfentryfile line 1

^
dpkg: error processing gnome-panel-data (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of gnome-panel:
 gnome-panel depends on gnome-panel-data (= 1:2.18.1-0ubuntu3.1); however:
  Package gnome-panel-data is not configured yet.
dpkg: error processing gnome-panel (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-control-center:
 gnome-control-center depends on libmetacity0 (>= 1:2.14); however:
  Package libmetacity0 is not configured yet.
dpkg: error processing gnome-control-center (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 desktop-base
 metacity
 libmetacity0
 gnome-panel-data
 gnome-panel
 gnome-control-center

```

---

### Post by elmick on 2008-03-01
and apt-get:

```

mick@mick-laptop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
7 not fully installed or removed.
Need to get 0B/471kB of archives.
After unpacking 0B of additional disk space will be used.
(Reading database ... 94148 files and directories currently installed.)
Preparing to replace metacity-common 1:2.18.2-0ubuntu1 (using .../metacity-common_1%3a2.18.2-0ubuntu1_all.deb) ...
Unpacking replacement metacity-common ...
/tmp/gconf-gg0a1p/temp.entries:107: parser error : Opening and ending tag mismatch: entry line 107 and key
y><schema_key>/schemas/apps/panel/objects/attached_toplevel_id</schema_key></key
                                                                               ^
/tmp/gconf-gg0a1p/temp.entries:111: parser error : Opening and ending tag mismatch: key line 107 and entry
</entry>
        ^
/tmp/gconf-gg0a1p/temp.entries:113: parser error : error parsing attribute name
<key><entrylist</key>
               ^
/tmp/gconf-gg0a1p/temp.entries:113: parser error : attributes construct error
<key><entrylist</key>
               ^
/tmp/gconf-gg0a1p/temp.entries:113: parser error : Couldn't find end of Start Tag entrylist line 113
<key><entrylist</key>
               ^
/tmp/gconf-gg0a1p/temp.entries:125: parser error : Opening and ending tag mismatch: entry line 125 and key
y><schema_key>/schemas/apps/panel/objects/attached_toplevel_id</schema_key></key
                                                                               ^
/tmp/gconf-gg0a1p/temp.entries:129: parser error : Opening and ending tag mismatch: key line 125 and entry
</entry>
        ^
/tmp/gconf-gg0a1p/temp.entries:137: parser error : Opening and ending tag mismatch: entry line 137 and key
y><schema_key>/schemas/apps/panel/objects/attached_toplevel_id</schema_key></key
                                                                               ^
/tmp/gconf-gg0a1p/temp.entries:141: parser error : Opening and ending tag mismatch: key line 137 and entry
</entry>
        ^
/tmp/gconf-gg0a1p/temp.entries:143: parser error : Opening and ending tag mismatch: entry line 143 and key
y><schema_key>/schemas/apps/panel/objects/attached_toplevel_id</schema_key></key
                                                                               ^
/tmp/gconf-gg0a1p/temp.entries:147: parser error : Opening and ending tag mismatch: key line 143 and entry
</entry>
        ^
/tmp/gconf-gg0a1p/temp.entries:161: parser error : Opening and ending tag mismatch: entry line 161 and key
y><schema_key>/schemas/apps/panel/objects/attached_toplevel_id</schema_key></key
                                                                               ^
/tmp/gconf-gg0a1p/temp.entries:165: parser error : Opening and ending tag mismatch: key line 161 and entry
</entry>
        ^
/tmp/gconf-gg0a1p/temp.entries:179: parser error : Opening and ending tag mismatch: entry line 179 and key
y><schema_key>/schemas/apps/panel/objects/attached_toplevel_id</schema_key></key
                                                                               ^
/tmp/gconf-gg0a1p/temp.entries:183: parser error : Opening and ending tag mismatch: key line 179 and entry
</entry>
        ^
/tmp/gconf-gg0a1p/temp.entries:197: parser error : Opening and ending tag mismatch: entry line 197 and key
y><schema_key>/schemas/apps/panel/objects/attached_toplevel_id</schema_key></key
                                                                               ^
/tmp/gconf-gg0a1p/temp.entries:201: parser error : Opening and ending tag mismatch: key line 197 and entry
</entry>
        ^
/tmp/gconf-gg0a1p/temp.entries:209: parser error : error parsing attribute name
<key><list</key>
          ^
/tmp/gconf-gg0a1p/temp.entries:209: parser error : attributes construct error
<key><list</key>
          ^
/tmp/gconf-gg0a1p/temp.entries:209: parser error : Couldn't find end of Start Tag list line 209
<key><list</key>
          ^
/tmp/gconf-gg0a1p/temp.entries:215: parser error : Opening and ending tag mismatch: entry line 215 and key
y><schema_key>/schemas/apps/panel/objects/attached_toplevel_id</schema_key></key
                                                                               ^
/tmp/gconf-gg0a1p/temp.entries:219: parser error : Opening and ending tag mismatch: key line 215 and entry
</entry>
        ^
/tmp/gconf-gg0a1p/temp.entries:227: parser error : Opening and ending tag mismatch: entry line 227 and key
y><schema_key>/schemas/apps/panel/objects/attached_toplevel_id</schema_key></key
                                                                               ^
/tmp/gconf-gg0a1p/temp.entries:231: parser error : Opening and ending tag mismatch: key line 227 and entry
</entry>
        ^
/tmp/gconf-gg0a1p/temp.entries:267: parser error : Comment not terminated 
<!--</key>
<value>
  <string>TrashApplet Applet 
  <string>TrashApplet Applet --&gt;</string>
                             ^
/tmp/gconf-gg0a1p/temp.entries:356: parser error : Comment not terminated

^
/tmp/gconf-gg0a1p/temp.entries:356: parser error : Premature end of data in tag key line 265

^
/tmp/gconf-gg0a1p/temp.entries:356: parser error : Premature end of data in tag entry line 264

^
/tmp/gconf-gg0a1p/temp.entries:356: parser error : Premature end of data in tag entry line 226

^
/tmp/gconf-gg0a1p/temp.entries:356: parser error : Premature end of data in tag entry line 214

^
/tmp/gconf-gg0a1p/temp.entries:356: parser error : Premature end of data in tag entry line 196

^
/tmp/gconf-gg0a1p/temp.entries:356: parser error : Premature end of data in tag entry line 178

^
/tmp/gconf-gg0a1p/temp.entries:356: parser error : Premature end of data in tag entry line 160

^
/tmp/gconf-gg0a1p/temp.entries:356: parser error : Premature end of data in tag entry line 142

^
/tmp/gconf-gg0a1p/temp.entries:356: parser error : Premature end of data in tag entry line 136

^
/tmp/gconf-gg0a1p/temp.entries:356: parser error : Premature end of data in tag entry line 124

^
/tmp/gconf-gg0a1p/temp.entries:356: parser error : Premature end of data in tag entry line 106

^
/tmp/gconf-gg0a1p/temp.entries:356: parser error : Premature end of data in tag entrylist line 2

^
/tmp/gconf-gg0a1p/temp.entries:356: parser error : Premature end of data in tag gconfentryfile line 1

^
dpkg: warning - old post-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
/tmp/gconf-IIekCZ/temp.entries:107: parser error : Opening and ending tag mismatch: entry line 107 and key
y><schema_key>/schemas/apps/panel/objects/attached_toplevel_id</schema_key></key
                                                                               ^
/tmp/gconf-IIekCZ/temp.entries:111: parser error : Opening and ending tag mismatch: key line 107 and entry
</entry>
        ^
/tmp/gconf-IIekCZ/temp.entries:113: parser error : error parsing attribute name
<key><entrylist</key>
               ^
/tmp/gconf-IIekCZ/temp.entries:113: parser error : attributes construct error
<key><entrylist</key>
               ^
/tmp/gconf-IIekCZ/temp.entries:113: parser error : Couldn't find end of Start Tag entrylist line 113
<key><entrylist</key>
               ^
/tmp/gconf-IIekCZ/temp.entries:125: parser error : Opening and ending tag mismatch: entry line 125 and key
y><schema_key>/schemas/apps/panel/objects/attached_toplevel_id</schema_key></key
                                                                               ^
/tmp/gconf-IIekCZ/temp.entries:129: parser error : Opening and ending tag mismatch: key line 125 and entry
</entry>
        ^
/tmp/gconf-IIekCZ/temp.entries:137: parser error : Opening and ending tag mismatch: entry line 137 and key
y><schema_key>/schemas/apps/panel/objects/attached_toplevel_id</schema_key></key
                                                                               ^
/tmp/gconf-IIekCZ/temp.entries:141: parser error : Opening and ending tag mismatch: key line 137 and entry
</entry>
        ^
/tmp/gconf-IIekCZ/temp.entries:143: parser error : Opening and ending tag mismatch: entry line 143 and 
</entry>
        ^
/tmp/gconf-IIekCZ/temp.entries:161: parser error : Opening and ending tag mismatch: entry line 161 and key
y><schema_key>/schemas/apps/panel/objects/attached_toplevel_id</schema_key></key
                                                                               ^
/tmp/gconf-IIekCZ/temp.entries:165: parser error : Opening and ending tag mismatch: key line 161 and entry
</entry>
        ^
/tmp/gconf-IIekCZ/temp.entries:179: parser error : Opening and ending tag mismatch: entry line 179 and key
y><schema_key>/schemas/apps/panel/objects/attached_toplevel_id</schema_key></key
                                                                               ^
/tmp/gconf-IIekCZ/temp.entries:183: parser error : Opening and ending tag mismatch: key line 179 and entry
</entry>
        ^
/tmp/gconf-IIekCZ/temp.entries:197: parser error : Opening and ending tag mismatch: entry line 197 and key
y><schema_key>/schemas/apps/panel/objects/attached_toplevel_id</schema_key></key
                                                                               ^
/tmp/gconf-IIekCZ/temp.entries:201: parser error : Opening and ending tag mismatch: key line 197 and entry
</entry>
        ^
/tmp/gconf-IIekCZ/temp.entries:209: parser error : error parsing attribute name
<key><list</key>
          ^
/tmp/gconf-IIekCZ/temp.entries:209: parser error : attributes construct error
<key><list</key>
          ^
/tmp/gconf-IIekCZ/temp.entries:209: parser error : Couldn't find end of Start Tag list line 209
<key><list</key>
          ^
/tmp/gconf-IIekCZ/temp.entries:215: parser error : Opening and ending tag mismatch: entry line 215 and key
y><schema_key>/schemas/apps/panel/objects/attached_toplevel_id</schema_key></key
                                                                               ^
/tmp/gconf-IIekCZ/temp.entries:219: parser error : Opening and ending tag mismatch: key line 215 and entry
</entry>
        ^
/tmp/gconf-IIekCZ/temp.entries:227: parser error : Opening and ending tag mismatch: entry line 227 and key
y><schema_key>/schemas/apps/panel/objects/attached_toplevel_id</schema_key></key
                                                                               ^
/tmp/gconf-IIekCZ/temp.entries:231: parser error : Opening and ending tag mismatch: key line 227 and entry
try
</entry>
        ^
/tmp/gconf-IIekCZ/temp.entries:267: parser error : Comment not terminated 
<!--</key>
<value>
  <string>TrashApplet Applet 
  <string>TrashApplet Applet --&gt;</string>
                             ^
/tmp/gconf-IIekCZ/temp.entries:356: parser error : Comment not terminated

^
/tmp/gconf-IIekCZ/temp.entries:356: parser error : Premature end of data in tag key line 265

^
/tmp/gconf-IIekCZ/temp.entries:356: parser error : Premature end of data in tag entry line 264

^
/tmp/gconf-IIekCZ/temp.entries:356: parser error : Premature end of data in tag entry line 226

^
/tmp/gconf-IIekCZ/temp.entries:356: parser error : Premature end of data in tag entry line 214

^
/tmp/gconf-IIekCZ/temp.entries:356: parser error : Premature end of data in tag entry line 196

^
/tmp/gconf-IIekCZ/temp.entries:356: parser error : Premature end of data in tag entry line 178

^
/tmp/gconf-IIekCZ/temp.entries:356: parser error : Premature end of data in tag entry line 160

^
/tmp/gconf-IIekCZ/temp.entries:356: parser error : Premature end of data in tag entry line 142

^
/tmp/gconf-IIekCZ/temp.entries:356: parser error : Premature end of data in tag entry line 136

^
/tmp/gconf-IIekCZ/temp.entries:356: parser error : Premature end of data in tag entry line 124

^
/tmp/gconf-IIekCZ/temp.entries:356: parser error : Premature end of data in tag entry line 106

^
/tmp/gconf-IIekCZ/temp.entries:356: parser error : Premature end of data in tag entrylist line 2

^
/tmp/gconf-IIekCZ/temp.entries:356: parser error : Premature end of data in tag gconfentryfile line 1

^
dpkg: error processing /var/cache/apt/archives/metacity-common_1%3a2.18.2-0ubuntu1_all.deb (--unpack):
 subprocess new post-removal script returned error exit status 1
/tmp/gconf-BWBOwA/temp.entries:107: parser error : Opening and ending tag mismatch: entry line 107 and key
y><schema_key>/schemas/apps/panel/objects/attached_toplevel_id</schema_key></key
                                                                               ^
/tmp/gconf-BWBOwA/temp.entries:111: parser error : Opening and ending tag mismatch: key line 107 and entry
</entry>
        ^
/tmp/gconf-BWBOwA/temp.entries:113: parser error : error parsing attribute name
<key><entrylist</key>
               ^
/tmp/gconf-BWBOwA/temp.entries:113: parser error : attributes construct error
<key><entrylist</key>
               ^
/tmp/gconf-BWBOwA/temp.entries:113: parser error : Couldn't find end of Start Tag entrylist line 113
<key><entrylist</key>
               ^
/tmp/gconf-BWBOwA/temp.entries:125: parser error : Opening and ending tag mismatch: entry line 125 and key
y><schema_key>/schemas/apps/panel/objects/attached_toplevel_id</schema_key></key
                                                                               ^
/tmp/gconf-BWBOwA/temp.entries:129: parser error : Opening and ending tag mismatch: key line 125 and entry
</entry>
        ^
/tmp/gconf-BWBOwA/temp.entries:137: parser error : Opening and ending tag mismatch: entry line 137 and key
y><schema_key>/schemas/apps/panel/objects/attached_toplevel_id</schema_key></key
                                                                               ^
/tmp/gconf-BWBOwA/temp.entries:141: parser error : Opening and ending tag mismatch: key line 137 and entry
</entry>
        ^
/tmp/gconf-BWBOwA/temp.entries:143: parser error : Opening and ending tag mismatch: entry line 143 and key
y><schema_key>/schemas/apps/panel/objects/attached_toplevel_id</schema_key></key
                                                                               ^
/tmp/gconf-BWBOwA/temp.entries:147: parser error : Opening and ending tag mismatch: key line 143 and entry
</entry>
        ^
/tmp/gconf-BWBOwA/temp.entries:161: parser error : Opening and ending tag mismatch: entry line 161 and key
y><schema_key>/schemas/apps/panel/objects/attached_toplevel_id</schema_key></key
                                                                               ^
/tmp/gconf-BWBOwA/temp.entries:165: parser error : Opening and ending tag mismatch: key line 161 and entry
</entry>
        ^
/tmp/gconf-BWBOwA/temp.entries:179: parser error : Opening and ending tag mismatch: entry line 179 and key
y><schema_key>/schemas/apps/panel/objects/attached_toplevel_id</schema_key></key
                                                                               ^
/tmp/gconf-BWBOwA/temp.entries:183: parser error : Opening and ending tag mismatch: key line 179 and entry
</entry>
        ^
/tmp/gconf-BWBOwA/temp.entries:197: parser error : Opening and ending tag mismatch: entry line 197 and key
y><schema_key>/schemas/apps/panel/objects/attached_toplevel_id</schema_key></key
                                                                               ^
/tmp/gconf-BWBOwA/temp.entries:201: parser error : Opening and ending tag mismatch: key line 197 and entry
</entry>
        ^
/tmp/gconf-BWBOwA/temp.entries:209: parser error : error parsing attribute name
<key><list</key>
          ^
/tmp/gconf-BWBOwA/temp.entries:209: parser error : attributes construct error
<key><list</key>
          ^
/tmp/gconf-BWBOwA/temp.entries:209: parser error : Couldn't find end of Start Tag list line 209
<key><list</key>
          ^
/tmp/gconf-BWBOwA/temp.entries:215: parser error : Opening and ending tag mismatch: entry line 215 and key
y><schema_key>/schemas/apps/panel/objects/attached_toplevel_id</schema_key></key
                                                                               ^
/tmp/gconf-BWBOwA/temp.entries:219: parser error : Opening and ending tag mismatch: key line 215 and entry
</entry>
        ^
/tmp/gconf-BWBOwA/temp.entries:227: parser error : Opening and ending tag mismatch: entry line 227 and key
y><schema_key>/schemas/apps/panel/objects/attached_toplevel_id</schema_key></key
                                                                               ^
/tmp/gconf-BWBOwA/temp.entries:231: parser error : Opening and ending tag mismatch: key line 227 and entry
</entry>
        ^
/tmp/gconf-BWBOwA/temp.entries:267: parser error : Comment not terminated 
<!--</key>
<value>
  <string>TrashApplet Applet 
  <string>TrashApplet Applet --&gt;</string>
                             ^
/tmp/gconf-BWBOwA/temp.entries:356: parser error : Comment not terminated

^
/tmp/gconf-BWBOwA/temp.entries:356: parser error : Premature end of data in tag key line 265

^
/tmp/gconf-BWBOwA/temp.entries:356: parser error : Premature end of data in tag entry line 264

^
/tmp/gconf-BWBOwA/temp.entries:356: parser error : Premature end of data in tag entry line 226

^
/tmp/gconf-BWBOwA/temp.entries:356: parser error : Premature end of data in tag entry line 214

^
/tmp/gconf-BWBOwA/temp.entries:356: parser error : Premature end of data in tag entry line 196

^
/tmp/gconf-BWBOwA/temp.entries:356: parser error : Premature end of data in tag entry line 178

^
/tmp/gconf-BWBOwA/temp.entries:356: parser error : Premature end of data in tag entry line 160

^
/tmp/gconf-BWBOwA/temp.entries:356: parser error : Premature end of data in tag entry line 142

^
/tmp/gconf-BWBOwA/temp.entries:356: parser error : Premature end of data in tag entry line 136

^
/tmp/gconf-BWBOwA/temp.entries:356: parser error : Premature end of data in tag entry line 124

^
/tmp/gconf-BWBOwA/temp.entries:356: parser error : Premature end of data in tag entry line 106

^
/tmp/gconf-BWBOwA/temp.entries:356: parser error : Premature end of data in tag entrylist line 2

^
/tmp/gconf-BWBOwA/temp.entries:356: parser error : Premature end of data in tag gconfentryfile line 1

^
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/metacity-common_1%3a2.18.2-0ubuntu1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
mick@mick-laptop:~$ 

```

---

### Post by zvacet on 2008-03-01
```
sudo apt-get install --reinstall metacity-common
```

```
sudo dpkg --configure -a
```

---

### Post by elmick on 2008-03-01
> **zvacet said:**
> ```
sudo apt-get install --reinstall metacity-common
```

```
sudo dpkg --configure -a
```

Hi,

I get the same error when I try this.

Is it not maybe something to do with /tmp/gconf... ? i dont know whats going on, has anyone had this type of problem before ?

thanks.

---

### Post by zvacet on 2008-03-01
```
sudo dpkg --configure  metacity
```

Use same command for gnome-panel  gnome-control-center  libmetacity0 desktop-base gnome-panel-data

---

### Post by elmick on 2008-03-02
> **zvacet said:**
> ```
sudo dpkg --configure  metacity
```

Use same command for gnome-panel  gnome-control-center  libmetacity0 desktop-base gnome-panel-data

is that not the same as --configure -a?


mick@mick-laptop:~$ sudo dpkg --configure gnome-panel-data
```


Setting up gnome-panel-data (2.18.1-0ubuntu3.1) ...
laptop configuration
/tmp/gconf-6QfQXQ/temp.entries:107: parser error : Opening and ending tag misma
ch: entry line 107 and key
y><schema_key>/schemas/apps/panel/objects/attached_toplevel_id</schema_key></ke
                                                                               
/tmp/gconf-6QfQXQ/temp.entries:111: parser error : Opening and ending tag misma
ch: key line 107 and entry
</entry>
        ^
/tmp/gconf-6QfQXQ/temp.entries:113: parser error : error parsing attribute name
<key><entrylist</key>
               ^
/tmp/gconf-6QfQXQ/temp.entries:113: parser error : attributes construct error
<key><entrylist</key>
               ^
/tmp/gconf-6QfQXQ/temp.entries:113: parser error : Couldn't find end of Start T
g entrylist line 113
<key><entrylist</key>
               ^
/tmp/gconf-6QfQXQ/temp.entries:125: parser error : Opening and ending tag misma
ch: entry line 125 and key
y><schema_key>/schemas/apps/panel/objects/attached_toplevel_id</schema_key></ke
                                                                               
/tmp/gconf-6QfQXQ/temp.entries:129: parser error : Opening and ending tag misma
ch: key line 125 and entry
</entry>
        ^
/tmp/gconf-6QfQXQ/temp.entries:137: parser error : Opening and ending tag misma
ch: entry line 137 and key
y><schema_key>/schemas/apps/panel/objects/attached_toplevel_id</schema_key></ke
                                                                               
/tmp/gconf-6QfQXQ/temp.entries:141: parser error : Opening and ending tag misma
ch: key line 137 and entry
</entry>
        ^
/tmp/gconf-6QfQXQ/temp.entries:143: parser error : Opening and ending tag misma
ch: entry line 143 and key
y><schema_key>/schemas/apps/panel/objects/attached_toplevel_id</schema_key></ke
                                                                               
/tmp/gconf-6QfQXQ/temp.entries:147: parser error : Opening and ending tag misma
ch: key line 143 and entry
</entry>
        ^
/tmp/gconf-6QfQXQ/temp.entries:161: parser error : Opening and ending tag misma
ch: entry line 161 and key
y><schema_key>/schemas/apps/panel/objects/attached_toplevel_id</schema_key></ke
                                                                               
/tmp/gconf-6QfQXQ/temp.entries:165: parser error : Opening and ending tag misma
ch: key line 161 and entry
</entry>
        ^
/tmp/gconf-6QfQXQ/temp.entries:179: parser error : Opening and ending tag misma
ch: entry line 179 and key
y><schema_key>/schemas/apps/panel/objects/attached_toplevel_id</schema_key></ke
                                                                               
/tmp/gconf-6QfQXQ/temp.entries:183: parser error : Opening and ending tag misma
ch: key line 179 and entry
</entry>
        ^
/tmp/gconf-6QfQXQ/temp.entries:197: parser error : Opening and ending tag misma
ch: entry line 197 and key
y><schema_key>/schemas/apps/panel/objects/attached_toplevel_id</schema_key></ke
                                                                               
/tmp/gconf-6QfQXQ/temp.entries:201: parser error : Opening and ending tag misma
ch: key line 197 and entry
</entry>
        ^
/tmp/gconf-6QfQXQ/temp.entries:209: parser error : error parsing attribute name
<key><list</key>
          ^
/tmp/gconf-6QfQXQ/temp.entries:209: parser error : attributes construct error
<key><list</key>
          ^
/tmp/gconf-6QfQXQ/temp.entries:209: parser error : Couldn't find end of Start T
g list line 209
<key><list</key>
          ^
/tmp/gconf-6QfQXQ/temp.entries:215: parser error : Opening and ending tag misma
ch: entry line 215 and key
y><schema_key>/schemas/apps/panel/objects/attached_toplevel_id</schema_key></ke
                                                                               
/tmp/gconf-6QfQXQ/temp.entries:219: parser error : Opening and ending tag misma
ch: key line 215 and entry
</entry>
        ^
/tmp/gconf-6QfQXQ/temp.entries:227: parser error : Opening and ending tag misma
ch: entry line 227 and key
y><schema_key>/schemas/apps/panel/objects/attached_toplevel_id</schema_key></ke
                                                                               
/tmp/gconf-6QfQXQ/temp.entries:231: parser error : Opening and ending tag misma
ch: key line 227 and entry
</entry>
        ^
/tmp/gconf-6QfQXQ/temp.entries:267: parser error : Comment not terminated 
<!--</key>
<value>
  <string>TrashApplet Applet 
  <string>TrashApplet Applet --&gt;</string>
                             ^
/tmp/gconf-6QfQXQ/temp.entries:356: parser error : Comment not terminated

^
/tmp/gconf-6QfQXQ/temp.entries:356: parser error : Premature end of data in tag
key line 265

^
/tmp/gconf-6QfQXQ/temp.entries:356: parser error : Premature end of data in tag
entry line 264

^
/tmp/gconf-6QfQXQ/temp.entries:356: parser error : Premature end of data in tag
entry line 226

^
/tmp/gconf-6QfQXQ/temp.entries:356: parser error : Premature end of data in tag
entry line 214

^
/tmp/gconf-6QfQXQ/temp.entries:356: parser error : Premature end of data in tag
entry line 196

^
/tmp/gconf-6QfQXQ/temp.entries:356: parser error : Premature end of data in tag
entry line 178

^
/tmp/gconf-6QfQXQ/temp.entries:356: parser error : Premature end of data in tag
entry line 160
^
/tmp/gconf-6QfQXQ/temp.entries:356: parser error : Premature end of data in tag
entry line 142

^
/tmp/gconf-6QfQXQ/temp.entries:356: parser error : Premature end of data in tag
entry line 136

^
/tmp/gconf-6QfQXQ/temp.entries:356: parser error : Premature end of data in tag
entry line 124

^
/tmp/gconf-6QfQXQ/temp.entries:356: parser error : Premature end of data in tag
entry line 106

^
/tmp/gconf-6QfQXQ/temp.entries:356: parser error : Premature end of data in tag
entrylist line 2

^
/tmp/gconf-6QfQXQ/temp.entries:356: parser error : Premature end of data in tag
gconfentryfile line 1

^
dpkg: error processing gnome-panel-data (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 gnome-panel-data
mick@mick-laptop:~$ 


```

mick@mick-laptop:~$ sudo dpkg --configure desktop-base
```

Setting up desktop-base (4.0.0) ...
/tmp/gconf-DrjP-s/temp.entries:107: parser error : Opening and ending tag mismatch: entry line 107 and key
y><schema_key>/schemas/apps/panel/objects/attached_toplevel_id</schema_key></key
                                                                               ^
/tmp/gconf-DrjP-s/temp.entries:111: parser error : Opening and ending tag mismatch: key line 107 and entry
</entry>
        ^
/tmp/gconf-DrjP-s/temp.entries:113: parser error : error parsing attribute name
<key><entrylist</key>
               ^
/tmp/gconf-DrjP-s/temp.entries:113: parser error : attributes construct error
<key><entrylist</key>
               ^
/tmp/gconf-DrjP-s/temp.entries:113: parser error : Couldn't find end of Start Tag entrylist line 113
<key><entrylist</key>
               ^
/tmp/gconf-DrjP-s/temp.entries:125: parser error : Opening and ending tag mismatch: entry line 125 and key
y><schema_key>/schemas/apps/panel/objects/attached_toplevel_id</schema_key></key
                                                                               ^
/tmp/gconf-DrjP-s/temp.entries:129: parser error : Opening and ending tag mismatch: key line 125 and entry
</entry>
        ^
/tmp/gconf-DrjP-s/temp.entries:137: parser error : Opening and ending tag mismatch: entry line 137 and key
y><schema_key>/schemas/apps/panel/objects/attached_toplevel_id</schema_key></key
                                                                               ^
/tmp/gconf-DrjP-s/temp.entries:141: parser error : Opening and ending tag mismatch: key line 137 and entry
</entry>
        ^
/tmp/gconf-DrjP-s/temp.entries:143: parser error : Opening and ending tag mismatch: entry line 143 and key
y><schema_key>/schemas/apps/panel/objects/attached_toplevel_id</schema_key></key
                                                                               ^
/tmp/gconf-DrjP-s/temp.entries:147: parser error : Opening and ending tag mismatch: key line 143 and entry
</entry>
        ^
/tmp/gconf-DrjP-s/temp.entries:161: parser error : Opening and ending tag mismatch: entry line 161 and key
y><schema_key>/schemas/apps/panel/objects/attached_toplevel_id</schema_key></key
                                                                               ^
/tmp/gconf-DrjP-s/temp.entries:165: parser error : Opening and ending tag mismatch: key line 161 and entry
</entry>
        ^
/tmp/gconf-DrjP-s/temp.entries:179: parser error : Opening and ending tag mismatch: entry line 179 and key
y><schema_key>/schemas/apps/panel/objects/attached_toplevel_id</schema_key></key
                                                                               ^
/tmp/gconf-DrjP-s/temp.entries:183: parser error : Opening and ending tag mismatch: key line 179 and entry
</entry>
        ^
/tmp/gconf-DrjP-s/temp.entries:197: parser error : Opening and ending tag mismatch: entry line 197 and key
y><schema_key>/schemas/apps/panel/objects/attached_toplevel_id</schema_key></key
                                                                               ^
/tmp/gconf-DrjP-s/temp.entries:201: parser error : Opening and ending tag mismatch: key line 197 and entry
</entry>
        ^
/tmp/gconf-DrjP-s/temp.entries:209: parser error : error parsing attribute name
<key><list</key>
          ^
/tmp/gconf-DrjP-s/temp.entries:209: parser error : attributes construct error
<key><list</key>
          ^
/tmp/gconf-DrjP-s/temp.entries:209: parser error : Couldn't find end of Start Tag list line 209
<key><list</key>
          ^
/tmp/gconf-DrjP-s/temp.entries:215: parser error : Opening and ending tag mismatch: entry line 215 and key
y><schema_key>/schemas/apps/panel/objects/attached_toplevel_id</schema_key></key
                                                                               ^
/tmp/gconf-DrjP-s/temp.entries:219: parser error : Opening and ending tag mismatch: key line 215 and entry
</entry>
        ^
/tmp/gconf-DrjP-s/temp.entries:227: parser error : Opening and ending tag mismatch: entry line 227 and key
y><schema_key>/schemas/apps/panel/objects/attached_toplevel_id</schema_key></key
                                                                               ^
/tmp/gconf-DrjP-s/temp.entries:231: parser error : Opening and ending tag mismatch: key line 227 and entry
</entry>
        ^
/tmp/gconf-DrjP-s/temp.entries:267: parser error : Comment not terminated 
<!--</key>
<value>
  <string>TrashApplet Applet 
  <string>TrashApplet Applet --&gt;</string>
                             ^
/tmp/gconf-DrjP-s/temp.entries:356: parser error : Comment not terminated

^
/tmp/gconf-DrjP-s/temp.entries:356: parser error : Premature end of data in tag key line 265

^
/tmp/gconf-DrjP-s/temp.entries:356: parser error : Premature end of data in tag entry line 264

^
/tmp/gconf-DrjP-s/temp.entries:356: parser error : Premature end of data in tag entry line 226

^
/tmp/gconf-DrjP-s/temp.entries:356: parser error : Premature end of data in tag entry line 214

^
/tmp/gconf-DrjP-s/temp.entries:356: parser error : Premature end of data in tag entry line 196

^
/tmp/gconf-DrjP-s/temp.entries:356: parser error : Premature end of data in tag entry line 178

^
/tmp/gconf-DrjP-s/temp.entries:356: parser error : Premature end of data in tag entry line 160

^
/tmp/gconf-DrjP-s/temp.entries:356: parser error : Premature end of data in tag entry line 142

^
/tmp/gconf-DrjP-s/temp.entries:356: parser error : Premature end of data in tag entry line 136

^
/tmp/gconf-DrjP-s/temp.entries:356: parser error : Premature end of data in tag entry line 124

^
/tmp/gconf-DrjP-s/temp.entries:356: parser error : Premature end of data in tag entry line 106

^
/tmp/gconf-DrjP-s/temp.entries:356: parser error : Premature end of data in tag entrylist line 2
^
/tmp/gconf-DrjP-s/temp.entries:356: parser error : Premature end of data in tag gconfentryfile line 1

^
dpkg: error processing desktop-base (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 desktop-base
mick@mick-laptop:~$ 



```

gnome-panel, gnome-control-center and libmetacity0 all just say they depend on something.

---

