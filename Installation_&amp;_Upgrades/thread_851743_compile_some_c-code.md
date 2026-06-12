---
title: "compile some c-code"
date: 2008-07-07
forum: Installation &amp; Upgrades
---

### Post by mvdberg112 on 2008-07-07
How do I compile a piece of software that I downloaded? All the code is included in c.
If anybody can help, thanks in advance!

[http://home.freeuk.net/igbarn/alarm-applet.html](http://home.freeuk.net/igbarn/alarm-applet.html) en I downloaded
[alarm-applet-0.8.9]("http://home.freeuk.net/igbarn/alarm-applet-0.8.9.tar.gz")

No ./configure is included.
A ./Makefile is present though.
The README does not give info on howto compile.
I have installed things like build-essential and read some howtos

```
make -f Makefile
```
gives:
```
#:/usr/local/src/alarm-applet-0.8.9# make -f Makefile 
cc `gnome-config --cflags applets` -DWITH_SOUND  -c alarm.c
/bin/sh: gnome-config: not found
In file included from alarm.c:1:
alarm_applet.h:6:19: error: gnome.h: No such file or directory
alarm_applet.h:7:27: error: applet-widget.h: No such file or directory
In file included from alarm.c:1:
alarm_applet.h:75: error: expected specifier-qualifier-list before ‘GtkWidget’
alarm_applet.h:107: error: expected specifier-qualifier-list before ‘GString’
alarm_applet.h:127: error: expected declaration specifiers or ‘...’ before ‘gchar’
alarm_applet.h:128: error: expected declaration specifiers or ‘...’ before ‘gchar’
alarm_applet.h:132: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
alarm_applet.h:133: error: expected ‘)’ before ‘id’
alarm_applet.h:134: error: expected ‘)’ before ‘id’
alarm_applet.h:135: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
alarm_applet.h:136: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
alarm_applet.h:140: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘redraw_timeout’
alarm_applet.h:141: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘timeout_func’
alarm_applet.h:143: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
alarm_applet.h:144: error: expected ‘)’ before ‘*’ token
alarm_applet.h:145: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
alarm_applet.h:146: error: expected ‘)’ before ‘*’ token
alarm_applet.h:159: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘get_sound_vol_level’
alarm_applet.h:160: error: expected ‘)’ before ‘vol’
alarm_applet.h:161: error: expected ‘)’ before ‘*’ token
alarm_applet.h:162: error: expected ‘)’ before ‘*’ token
alarm_applet.h:166: error: expected ‘)’ before ‘*’ token
alarm_applet.h:169: error: expected ‘)’ before ‘*’ token
alarm.c:16: error: expected specifier-qualifier-list before ‘GList’
alarm.c: In function ‘new_alarm’:
alarm.c:31: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘num’
alarm.c:31: error: ‘num’ undeclared (first use in this function)
alarm.c:31: error: (Each undeclared identifier is reported only once
alarm.c:31: error: for each function it appears in.)
alarm.c:32: error: expected expression before ‘Alarm’
alarm.c:32: warning: initialization makes pointer from integer without a cast
alarm.c:33: error: ‘Alarm’ has no member named ‘msg_txt’
alarm.c:34: error: ‘Alarm’ has no member named ‘command’
alarm.c:38: error: ‘Alarm’ has no member named ‘msg_set’
alarm.c:38: error: ‘FALSE’ undeclared (first use in this function)
alarm.c:39: error: ‘Alarm’ has no member named ‘command_set’
alarm.c:40: error: ‘Alarm’ has no member named ‘modal_dialog’
alarm.c:41: error: ‘Alarm’ has no member named ‘ref_count’
alarm.c:42: error: ‘Alarm’ has no member named ‘persistant’
alarm.c: In function ‘init_alarm_store’:
alarm.c:50: error: expected expression before ‘AlarmStore’
alarm.c:50: warning: assignment makes pointer from integer without a cast
alarm.c:51: error: ‘AlarmStore’ has no member named ‘alarms’
alarm.c:52: error: ‘AlarmStore’ has no member named ‘num_alarms’
alarm.c:53: error: ‘AlarmStore’ has no member named ‘num_persistant’
alarm.c: At top level:
alarm.c:57: error: expected ‘)’ before ‘*’ token
alarm.c:63: error: expected ‘)’ before ‘*’ token
alarm.c:86: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘compare_alarms’
alarm.c: In function ‘destroy_alarms’:
alarm.c:117: error: ‘GList’ undeclared (first use in this function)
alarm.c:117: error: ‘list’ undeclared (first use in this function)
alarm.c:118: error: ‘gint’ undeclared (first use in this function)
alarm.c:118: error: expected ‘;’ before ‘i’
alarm.c:119: error: ‘AlarmStore’ has no member named ‘alarms’
alarm.c:123: error: ‘Alarm’ has no member named ‘msg_set’
alarm.c:123: error: ‘Alarm’ has no member named ‘msg_txt’
alarm.c:123: error: ‘Alarm’ has no member named ‘msg_txt’
alarm.c:123: error: ‘TRUE’ undeclared (first use in this function)
alarm.c:123: error: ‘Alarm’ has no member named ‘command_set’
alarm.c:123: error: ‘Alarm’ has no member named ‘command’
alarm.c:123: error: ‘Alarm’ has no member named ‘command’
alarm.c:124: error: ‘i’ undeclared (first use in this function)
alarm.c:131: error: ‘AlarmStore’ has no member named ‘alarms’
alarm.c: At top level:
alarm.c:137: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
alarm.c:208: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
alarm.c: In function ‘add_alarm’:
alarm.c:274: error: ‘AlarmStore’ has no member named ‘num_alarms’
alarm.c:279: error: ‘TRUE’ undeclared (first use in this function)
alarm.c:283: error: ‘AlarmStore’ has no member named ‘alarms’
alarm.c:283: error: ‘AlarmStore’ has no member named ‘alarms’
alarm.c:283: error: ‘compare_alarms’ undeclared (first use in this function)
alarm.c:284: error: ‘AlarmStore’ has no member named ‘num_alarms’
alarm.c:285: error: ‘Alarm’ has no member named ‘persistant’
alarm.c:286: error: ‘AlarmStore’ has no member named ‘num_persistant’
alarm.c: In function ‘delete_alarm’:
alarm.c:294: error: ‘AlarmStore’ has no member named ‘alarms’
alarm.c:294: error: ‘AlarmStore’ has no member named ‘alarms’
alarm.c:295: error: ‘AlarmStore’ has no member named ‘num_alarms’
alarm.c:296: error: ‘Alarm’ has no member named ‘persistant’
alarm.c:297: error: ‘AlarmStore’ has no member named ‘num_persistant’
alarm.c:298: error: ‘Alarm’ has no member named ‘msg_set’
alarm.c:298: error: ‘Alarm’ has no member named ‘msg_txt’
alarm.c:298: error: ‘Alarm’ has no member named ‘msg_txt’
alarm.c:298: error: ‘TRUE’ undeclared (first use in this function)
alarm.c:298: error: ‘Alarm’ has no member named ‘command_set’
alarm.c:298: error: ‘Alarm’ has no member named ‘command’
alarm.c:298: error: ‘Alarm’ has no member named ‘command’
alarm.c: In function ‘activate_alarm’:
alarm.c:321: error: ‘Alarm’ has no member named ‘msg_set’
alarm.c:322: error: ‘Alarm’ has no member named ‘msg_txt’
alarm.c:322: error: ‘Alarm’ has no member named ‘modal_dialog’
alarm.c:325: error: ‘gchar’ undeclared (first use in this function)
alarm.c:325: error: ‘msg’ undeclared (first use in this function)
alarm.c:326: error: ‘Alarm’ has no member named ‘modal_dialog’
alarm.c:334: error: ‘Alarm’ has no member named ‘command_set’
alarm.c:336: error: ‘Alarm’ has no member named ‘command’
alarm.c:338: error: ‘str’ undeclared (first use in this function)
alarm.c:338: error: ‘Alarm’ has no member named ‘command’
alarm.c:339: error: ‘FALSE’ undeclared (first use in this function)
alarm.c: At top level:
alarm.c:348: error: expected declaration specifiers or ‘...’ before ‘gchar’
alarm.c: In function ‘alarm_set_msg’:
alarm.c:350: error: ‘msg’ undeclared (first use in this function)
alarm.c:356: error: ‘Alarm’ has no member named ‘msg_set’
alarm.c:358: error: ‘Alarm’ has no member named ‘msg_txt’
alarm.c:362: error: ‘Alarm’ has no member named ‘msg_txt’
alarm.c:363: error: ‘Alarm’ has no member named ‘msg_set’
alarm.c:363: error: ‘TRUE’ undeclared (first use in this function)
alarm.c: At top level:
alarm.c:368: error: expected declaration specifiers or ‘...’ before ‘gchar’
alarm.c: In function ‘alarm_set_command’:
alarm.c:370: error: ‘cmd’ undeclared (first use in this function)
alarm.c:376: error: ‘Alarm’ has no member named ‘command_set’
alarm.c:378: error: ‘Alarm’ has no member named ‘command’
alarm.c:382: error: ‘Alarm’ has no member named ‘command’
alarm.c:383: error: ‘Alarm’ has no member named ‘command_set’
alarm.c:383: error: ‘TRUE’ undeclared (first use in this function)
alarm.c: At top level:
alarm.c:388: error: expected ‘)’ before ‘id’
alarm.c:407: error: expected ‘)’ before ‘id’
alarm.c:426: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘timeout_func’
alarm.c:497: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
make: *** [alarm.o] Error 1
```


[http://ubuntuforums.org/showthread.php?t=323939](http://ubuntuforums.org/showthread.php?t=323939)
[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)
[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

---

### Post by localhost80 on 2008-07-07
You need to install the gnome-devel package

```

apt-get install gnome-devel

```

---

