---
title: "PIdgin crashing on message"
date: 2009-03-01
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by techdude3177 on 2009-03-01
anyone else having this problem? it just started today and i havnt updated...

this is the messages i get when i load pidgin and then send myself a message...

~$ pidgin
(pidgin:7186): pidgin-libnotify-plugin-DEBUG: Entering indicate_chat_nick

(pidgin:7186): pidgin-libnotify-plugin-WARNING **: Conversation is NULL, not sure what to do with that!

(pidgin:7186): pidgin-libnotify-plugin-WARNING **: Notify Message send has NULL Conversation, assuming hidden
(pidgin:7186): pidgin-libnotify-plugin-DEBUG: Entering indicate_chat_nick

(pidgin:7186): pidgin-libnotify-plugin-WARNING **: Pidgin conversation's widgets are in focus

(pidgin:7186): GStreamer-CRITICAL **: 
Trying to dispose element play, but it is not in the NULL state.
You need to explicitly set elements to the NULL state before
dropping the final reference, to allow them to clean up.


(pidgin:7186): GStreamer-CRITICAL **: gst_element_set_state: assertion `GST_IS_ELEMENT (element)' failed

(pidgin:7186): GStreamer-CRITICAL **: gst_object_unref: assertion `((GObject *) object)->ref_count > 0' failed
Segmentation fault (core dumped)

---

