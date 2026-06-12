---
title: "Google gadgets"
date: 2010-04-18
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by joris1977 on 2010-04-18
Hi

I like the rss reader from google gadgets very much. But since a few days it doesn't want to start any-more. I get a pop up with the message:

Program can't start because it failed to load the following module(s):

js-script-runtime

On the command line I get:

Failed to find proper Gecko Runtime Environment!


If I start with ggl-gtk -l 0

than I get:

Initialize soup_xml_http_request extension.
Initialize default_framework extension.
Initialize libxml2_xml_parser extension.
Initialize default_options extension.
Initialize dbus_script_class extension.
Initialize gtk_edit_element extension.
Initialize gst_video_element extension.
Initialize gtk_system_framework extension.
Initialize gst_audio_framework extension.
Initialize linux_system_framework extension.
Initialize analytics_usage_collector extension.
Initialize google_gadget_manager extension.
Initialize smjs_script_runtime extension.
Failed to find proper Gecko Runtime Environment!
Finalize smjs_script_runtime extension.
Initialize gtkmoz_browser_element extension.
Initialize gtk_flash_element extension.
gtk_flash_element.cc:66: Finalize gtk_flash_element extension.
browser_element.cc:71: Finalize gtkmoz_browser_element extension.
google_gadget_manager_init.cc:32: Finalize google_gadget_manager extension.
analytics_usage_collector.cc:254: Finalize analytics_usage_collector extension.
linux_system_framework.cc:125: Finalize linux_system_framework extension.
gst_audio_framework.cc:480: Finalize gst_audio_framework extension.
gtk_system_framework.cc:344: Finalize gtk_system_framework extension.
gst_video_element.cc:47: Finalize gst_video_element extension.
gtk_edit_element.cc:42: Finalize gtk_edit_element extension.
dbus_script_class.cc:65: Finalize dbus_script_class extension.
default_options.cc:487: Finalize default_options extension.
libxml2_xml_parser.cc:866: Finalize libxml2_xml_parser extension.
default_framework.cc:413: Finalize default_framework extension.
soup_xml_http_request.cc:1160: Finalize soup_xml_http_request extension.

I am not sure if this is a bug in Lucid, because I couldn't find any bug reports about other users experiencing this in Lucid. 

Is anybody else experiencing this and how can I troubleshoot further?

---

### Post by joris1977 on 2010-04-20
Nobody has this issue?

---

### Post by davidmohammed on 2010-04-20
no works like a charm here - 32 bit lucid.  Googling - same error reported for 64bit fedora - are you running 64bit lucid?

---

### Post by joris1977 on 2010-04-20
Thanks for your reply.

Yes I am running 64 bit lucid. It was working fine at first, but some update killed it. I am not sure which one though. Do you have a link to that fedora bug? I have been googling, but I only found similar bug reports from a few years ago...

---

### Post by davidmohammed on 2010-04-20
... this is the [link]("http://forums.fedoraforum.org/showthread.php?t=226922") I was looking at from july last year

---

### Post by joris1977 on 2010-04-20
Thanks for the link. Well it looks like it is probably a bug and not something weird in my configuration. I will wait a few days see if an update fixes it. If not I will make a bug report.

---

### Post by davidmohammed on 2010-04-21
> **joris1977 said:**
> Thanks for the link. Well it looks like it is probably a bug and not something weird in my configuration. I will wait a few days see if an update fixes it. If not I will make a bug report.

probably worth making the bug report on the upstream code.google.com site not on launchpad - as far as I can see, lucid is using the same version as upstream.  Once fixed by the devs upstream, file a bug on launchpad to get the update into lucid/meerkat

---

### Post by little_penguin on 2010-04-26
I am currently running Jaunty and I have been getting the same error message from Google Gadgets over the last few days.

---

