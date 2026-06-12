---
title: "Firefox Seg Fault Core Dumped"
date: 2008-08-06
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by eeclark on 2008-08-06
Anyone else having this problem with Firefox when going to a site with Java?

I searched the forum with "Firefox Seg Fault" and "Firefox Core Dumped" ...it returned "Sorry - no matches. Please try some different terms."

---

### Post by eeclark on 2008-08-07
I have tried Opera and it does not crash like Firefox did when trying to access a page with Java.

---

### Post by philinux on 2008-08-07
Yes. I've noticed there's also a new pop up. Screen shot attached. No idea where it stores this though. I'm off to launchpad with it now.

```
 firefox -safe-mode
GCJ PLUGIN: thread 0x6647f0: NP_Initialize
GCJ PLUGIN: thread 0x6647f0: NP_Initialize: using /usr/lib/classpath/gappletviewer.
GCJ PLUGIN: thread 0x6647f0: NP_Initialize return
GCJ PLUGIN: thread 0x6647f0: GCJ_New
GCJ PLUGIN: thread 0x6647f0: plugin_data_new
GCJ PLUGIN: thread 0x6647f0: plugin_data_new return
GCJ PLUGIN: thread 0x6647f0: plugin_get_documentbase
GCJ PLUGIN: thread 0x6647f0: plugin_get_documentbase return
gcjwebplugin.cc:978: thread 0x6647f0: Error: Failed to read line from whitelist file.
GCJ PLUGIN: thread 0x6647f0: GCJ_New
GCJ PLUGIN: thread 0x6647f0: plugin_data_new
GCJ PLUGIN: thread 0x6647f0: plugin_data_new return
GCJ PLUGIN: thread 0x6647f0: plugin_get_documentbase
GCJ PLUGIN: thread 0x6647f0: plugin_get_documentbase return
GCJ PLUGIN: thread 0x6647f0: plugin_start_appletviewer
GCJ PLUGIN: thread 0x6647f0: plugin_start_appletviewer return
GCJ PLUGIN: thread 0x6647f0: GCJ_New: got confirmation that appletviewer is running.
GCJ PLUGIN: thread 0x6647f0: plugin_create_applet_tag
GCJ PLUGIN: thread 0x6647f0: plugin_create_applet_tag return
GCJ PLUGIN: thread 0x6647f0: plugin_send_message_to_appletviewer
  PIPE: plugin wrote instance-5418-1
GCJ PLUGIN: thread 0x6647f0: plugin_send_message_to_appletviewer return
GCJ PLUGIN: thread 0x6647f0: plugin_send_message_to_appletviewer
  PIPE: plugin wrote tag http://www.java.com/en/download/help/testvm.xml?ff3 <EMBED CODE="testvmDynamicJavaComPopUp819.class" CODEBASE="../../../applet" HEIGHT="300" WIDTH="390" ><PARAM NAME="alt" VALUE="Java Runtime Environment is not working on your system"><PARAM NAME="border" VALUE="0"></EMBED>
GCJ PLUGIN: thread 0x6647f0: plugin_send_message_to_appletviewer return
GCJ PLUGIN: thread 0x6647f0: GCJ_New return
GCJ PLUGIN: thread 0x6647f0: NP_GetValue
GCJ PLUGIN: thread 0x6647f0: NP_GetValue: returning plugin description.
GCJ PLUGIN: thread 0x6647f0: NP_GetValue return
GCJ PLUGIN: thread 0x6647f0: GCJ_GetValue
GCJ PLUGIN: thread 0x6647f0: GCJ_GetValue: returning TRUE for NeedsXEmbed.
GCJ PLUGIN: thread 0x6647f0: GCJ_GetValue return
GCJ PLUGIN: thread 0x6647f0: GCJ_SetWindow
GCJ PLUGIN: thread 0x6647f0: GCJ_SetWindow: setting window.
GCJ PLUGIN: thread 0x6647f0: plugin_send_message_to_appletviewer
  PIPE: plugin wrote instance-5418-1
GCJ PLUGIN: thread 0x6647f0: plugin_send_message_to_appletviewer return
GCJ PLUGIN: thread 0x6647f0: plugin_send_message_to_appletviewer
  PIPE: plugin wrote handle 48237403
GCJ PLUGIN: thread 0x6647f0: plugin_send_message_to_appletviewer return
GCJ PLUGIN: thread 0x6647f0: GCJ_SetWindow return
GCJ PLUGIN: thread 0x6647f0: GCJ_SetWindow
GCJ PLUGIN: thread 0x6647f0: GCJ_SetWindow: window already exists.
GCJ PLUGIN: thread 0x6647f0: GCJ_SetWindow: window width changed.
GCJ PLUGIN: thread 0x6647f0: plugin_send_message_to_appletviewer
  PIPE: plugin wrote instance-5418-1
GCJ PLUGIN: thread 0x6647f0: plugin_send_message_to_appletviewer return
GCJ PLUGIN: thread 0x6647f0: plugin_send_message_to_appletviewer
  PIPE: plugin wrote width 390
GCJ PLUGIN: thread 0x6647f0: plugin_send_message_to_appletviewer return
GCJ PLUGIN: thread 0x6647f0: GCJ_SetWindow: window height changed.
GCJ PLUGIN: thread 0x6647f0: plugin_send_message_to_appletviewer
  PIPE: plugin wrote instance-5418-1
GCJ PLUGIN: thread 0x6647f0: plugin_send_message_to_appletviewer return
GCJ PLUGIN: thread 0x6647f0: plugin_send_message_to_appletviewer
  PIPE: plugin wrote height 300
GCJ PLUGIN: thread 0x6647f0: plugin_send_message_to_appletviewer return
GCJ PLUGIN: thread 0x6647f0: GCJ_SetWindow return
  PIPE: applet viewer wrote:running
  PIPE: applet viewer read:instance-5418-1
  PIPE: applet viewer read:tag http://www.java.com/en/download/help/testvm.xml?ff3 <EMBED CODE="testvmDynamicJavaComPopUp819.class" CODEBASE="../../../applet" HEIGHT="300" WIDTH="390" ><PARAM NAME="alt" VALUE="Java Runtime Environment is not working on your system"><PARAM NAME="border" VALUE="0"></EMBED>
  PIPE: applet viewer read:instance-5418-1
  PIPE: applet viewer read:handle 48237403
TestVM 8.18 sc
Copyright (c) 2008 Sun Microsystems, Inc.
All Rights Reserved.
Current JRE version set in file: 607
 
Cmd Line Java -version:   Java 4  update  0
 
Your JRE version number-javaVersionInt:   400
Current JRE version on Java.com - currentJREinTextInt: 607
Your Operating System:   linux
Your OS Version:   2.6.26-5-generic
Your system architecture: amd64
  PIPE: applet viewer read:instance-5418-1
  PIPE: applet viewer read:width 390
  PIPE: applet viewer read:instance-5418-1
  PIPE: applet viewer read:height 300
GCJ PLUGIN: thread 0x6647f0: plugin_start_appletviewer
GCJ PLUGIN: thread 0x6647f0: plugin_start_appletviewer return
GCJ PLUGIN: thread 0x6647f0: GCJ_New: got confirmation that appletviewer is running.
GCJ PLUGIN: thread 0x6647f0: plugin_create_applet_tag
GCJ PLUGIN: thread 0x6647f0: plugin_create_applet_tag return
GCJ PLUGIN: thread 0x6647f0: plugin_send_message_to_appletviewer
  PIPE: plugin wrote instance-5418-0
GCJ PLUGIN: thread 0x6647f0: plugin_send_message_to_appletviewer return
GCJ PLUGIN: thread 0x6647f0: plugin_send_message_to_appletviewer
  PIPE: plugin wrote tag http://www.java.com/en/download/installed.jsp?detect=jre&try=1 <EMBED CODE="jreCheck.class" CODEBASE="/jsp_utils/" HEIGHT="2" WIDTH="1" ><PARAM NAME="type" VALUE="application/x-java-applet"><PARAM NAME="jumpto" VALUE="/en/download/installed.jsp?"><PARAM NAME="pause" VALUE="2000"></EMBED>
GCJ PLUGIN: thread 0x6647f0: plugin_send_message_to_appletviewer return
GCJ PLUGIN: thread 0x6647f0: GCJ_New return
  PIPE: applet viewer wrote:running
  PIPE: applet viewer read:instance-5418-0
  PIPE: applet viewer read:tag http://www.java.com/en/download/installed.jsp?detect=jre&try=1 <EMBED CODE="jreCheck.class" CODEBASE="/jsp_utils/" HEIGHT="2" WIDTH="1" ><PARAM NAME="type" VALUE="application/x-java-applet"><PARAM NAME="jumpto" VALUE="/en/download/installed.jsp?"><PARAM NAME="pause" VALUE="2000"></EMBED>
  PIPE: applet viewer read:null
appletviewer: exiting plugin appletviewer
  PIPE: applet viewer read:null
appletviewer: exiting plugin appletviewer
Segmentation fault (core dumped)
```

---

### Post by eeclark on 2008-08-07
> **philinux said:**
> Yes. I've noticed there's also a new pop up. Screen shot attached. No idea where it stores this though. I'm off to launchpad with it now.

```
 firefox -safe-mode
GCJ PLUGIN: thread 0x6647f0: NP_Initialize
GCJ PLUGIN: thread 0x6647f0: NP_Initialize: using /usr/lib/classpath/gappletviewer.
GCJ PLUGIN: thread 0x6647f0: NP_Initialize return
GCJ PLUGIN: thread 0x6647f0: GCJ_New
GCJ PLUGIN: thread 0x6647f0: plugin_data_new
GCJ PLUGIN: thread 0x6647f0: plugin_data_new return
GCJ PLUGIN: thread 0x6647f0: plugin_get_documentbase
GCJ PLUGIN: thread 0x6647f0: plugin_get_documentbase return
gcjwebplugin.cc:978: thread 0x6647f0: Error: Failed to read line from whitelist file.
GCJ PLUGIN: thread 0x6647f0: GCJ_New
GCJ PLUGIN: thread 0x6647f0: plugin_data_new
GCJ PLUGIN: thread 0x6647f0: plugin_data_new return
GCJ PLUGIN: thread 0x6647f0: plugin_get_documentbase
GCJ PLUGIN: thread 0x6647f0: plugin_get_documentbase return
GCJ PLUGIN: thread 0x6647f0: plugin_start_appletviewer
GCJ PLUGIN: thread 0x6647f0: plugin_start_appletviewer return
GCJ PLUGIN: thread 0x6647f0: GCJ_New: got confirmation that appletviewer is running.
GCJ PLUGIN: thread 0x6647f0: plugin_create_applet_tag
GCJ PLUGIN: thread 0x6647f0: plugin_create_applet_tag return
GCJ PLUGIN: thread 0x6647f0: plugin_send_message_to_appletviewer
  PIPE: plugin wrote instance-5418-1
GCJ PLUGIN: thread 0x6647f0: plugin_send_message_to_appletviewer return
GCJ PLUGIN: thread 0x6647f0: plugin_send_message_to_appletviewer
  PIPE: plugin wrote tag http://www.java.com/en/download/help/testvm.xml?ff3 <EMBED CODE="testvmDynamicJavaComPopUp819.class" CODEBASE="../../../applet" HEIGHT="300" WIDTH="390" ><PARAM NAME="alt" VALUE="Java Runtime Environment is not working on your system"><PARAM NAME="border" VALUE="0"></EMBED>
GCJ PLUGIN: thread 0x6647f0: plugin_send_message_to_appletviewer return
GCJ PLUGIN: thread 0x6647f0: GCJ_New return
GCJ PLUGIN: thread 0x6647f0: NP_GetValue
GCJ PLUGIN: thread 0x6647f0: NP_GetValue: returning plugin description.
GCJ PLUGIN: thread 0x6647f0: NP_GetValue return
GCJ PLUGIN: thread 0x6647f0: GCJ_GetValue
GCJ PLUGIN: thread 0x6647f0: GCJ_GetValue: returning TRUE for NeedsXEmbed.
GCJ PLUGIN: thread 0x6647f0: GCJ_GetValue return
GCJ PLUGIN: thread 0x6647f0: GCJ_SetWindow
GCJ PLUGIN: thread 0x6647f0: GCJ_SetWindow: setting window.
GCJ PLUGIN: thread 0x6647f0: plugin_send_message_to_appletviewer
  PIPE: plugin wrote instance-5418-1
GCJ PLUGIN: thread 0x6647f0: plugin_send_message_to_appletviewer return
GCJ PLUGIN: thread 0x6647f0: plugin_send_message_to_appletviewer
  PIPE: plugin wrote handle 48237403
GCJ PLUGIN: thread 0x6647f0: plugin_send_message_to_appletviewer return
GCJ PLUGIN: thread 0x6647f0: GCJ_SetWindow return
GCJ PLUGIN: thread 0x6647f0: GCJ_SetWindow
GCJ PLUGIN: thread 0x6647f0: GCJ_SetWindow: window already exists.
GCJ PLUGIN: thread 0x6647f0: GCJ_SetWindow: window width changed.
GCJ PLUGIN: thread 0x6647f0: plugin_send_message_to_appletviewer
  PIPE: plugin wrote instance-5418-1
GCJ PLUGIN: thread 0x6647f0: plugin_send_message_to_appletviewer return
GCJ PLUGIN: thread 0x6647f0: plugin_send_message_to_appletviewer
  PIPE: plugin wrote width 390
GCJ PLUGIN: thread 0x6647f0: plugin_send_message_to_appletviewer return
GCJ PLUGIN: thread 0x6647f0: GCJ_SetWindow: window height changed.
GCJ PLUGIN: thread 0x6647f0: plugin_send_message_to_appletviewer
  PIPE: plugin wrote instance-5418-1
GCJ PLUGIN: thread 0x6647f0: plugin_send_message_to_appletviewer return
GCJ PLUGIN: thread 0x6647f0: plugin_send_message_to_appletviewer
  PIPE: plugin wrote height 300
GCJ PLUGIN: thread 0x6647f0: plugin_send_message_to_appletviewer return
GCJ PLUGIN: thread 0x6647f0: GCJ_SetWindow return
  PIPE: applet viewer wrote:running
  PIPE: applet viewer read:instance-5418-1
  PIPE: applet viewer read:tag http://www.java.com/en/download/help/testvm.xml?ff3 <EMBED CODE="testvmDynamicJavaComPopUp819.class" CODEBASE="../../../applet" HEIGHT="300" WIDTH="390" ><PARAM NAME="alt" VALUE="Java Runtime Environment is not working on your system"><PARAM NAME="border" VALUE="0"></EMBED>
  PIPE: applet viewer read:instance-5418-1
  PIPE: applet viewer read:handle 48237403
TestVM 8.18 sc
Copyright (c) 2008 Sun Microsystems, Inc.
All Rights Reserved.
Current JRE version set in file: 607
 
Cmd Line Java -version:   Java 4  update  0
 
Your JRE version number-javaVersionInt:   400
Current JRE version on Java.com - currentJREinTextInt: 607
Your Operating System:   linux
Your OS Version:   2.6.26-5-generic
Your system architecture: amd64
  PIPE: applet viewer read:instance-5418-1
  PIPE: applet viewer read:width 390
  PIPE: applet viewer read:instance-5418-1
  PIPE: applet viewer read:height 300
GCJ PLUGIN: thread 0x6647f0: plugin_start_appletviewer
GCJ PLUGIN: thread 0x6647f0: plugin_start_appletviewer return
GCJ PLUGIN: thread 0x6647f0: GCJ_New: got confirmation that appletviewer is running.
GCJ PLUGIN: thread 0x6647f0: plugin_create_applet_tag
GCJ PLUGIN: thread 0x6647f0: plugin_create_applet_tag return
GCJ PLUGIN: thread 0x6647f0: plugin_send_message_to_appletviewer
  PIPE: plugin wrote instance-5418-0
GCJ PLUGIN: thread 0x6647f0: plugin_send_message_to_appletviewer return
GCJ PLUGIN: thread 0x6647f0: plugin_send_message_to_appletviewer
  PIPE: plugin wrote tag http://www.java.com/en/download/installed.jsp?detect=jre&try=1 <EMBED CODE="jreCheck.class" CODEBASE="/jsp_utils/" HEIGHT="2" WIDTH="1" ><PARAM NAME="type" VALUE="application/x-java-applet"><PARAM NAME="jumpto" VALUE="/en/download/installed.jsp?"><PARAM NAME="pause" VALUE="2000"></EMBED>
GCJ PLUGIN: thread 0x6647f0: plugin_send_message_to_appletviewer return
GCJ PLUGIN: thread 0x6647f0: GCJ_New return
  PIPE: applet viewer wrote:running
  PIPE: applet viewer read:instance-5418-0
  PIPE: applet viewer read:tag http://www.java.com/en/download/installed.jsp?detect=jre&try=1 <EMBED CODE="jreCheck.class" CODEBASE="/jsp_utils/" HEIGHT="2" WIDTH="1" ><PARAM NAME="type" VALUE="application/x-java-applet"><PARAM NAME="jumpto" VALUE="/en/download/installed.jsp?"><PARAM NAME="pause" VALUE="2000"></EMBED>
  PIPE: applet viewer read:null
appletviewer: exiting plugin appletviewer
  PIPE: applet viewer read:null
appletviewer: exiting plugin appletviewer
Segmentation fault (core dumped)
```

I did not get that when I went to 
[http://www.java.com/en/download/help/testvm.xml?ff3](http://www.java.com/en/download/help/testvm.xml?ff3)
It was successfull in bringing up the dancing java logo and system data.

---

### Post by philinux on 2008-08-07
Have run firefox from the terminal to see what it spits out?

---

