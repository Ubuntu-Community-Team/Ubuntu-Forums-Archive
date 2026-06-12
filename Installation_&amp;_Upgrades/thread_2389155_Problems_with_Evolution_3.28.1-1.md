---
title: "Problems with Evolution 3.28.1-1"
date: 2018-04-12
forum: Installation &amp; Upgrades
---

### Post by cigtoxdoc on 2018-04-12
When I upgraded from 16.04 LTS to 18.04 LTS, I received a new version of Evolution. I was involuntarily upgraded from 3.20.1 to 3.28.1-1.  Evolution 3.28.1-1 has some major bugs.  When I reply, the text of the message I am not replying to is NOT included.  The same problem occurs when I forward a message as inline.  Moreover, when I attempt to add a signature, I get broken pipe errors.  Please see output below when I started Evolution from the CLI.

How do I get a fully functional Evolution back???

John

johnl@john-Vostro-3500:~$ evolution

** (evolution:8478): CRITICAL **: 07:42:04.237: void webkit_web_view_load_bytes(WebKitWebView*, GBytes*, const char*, const char*, const char*): assertion 'bytesDataSize' failed

(evolution:8478): module-webkit-editor-WARNING **: 07:42:27.082: (/build/evolution-mc96o6/evolution-3.28.1/src/modules/webkit-editor/e-webkit-editor.c:5398):webkit_editor_finalize: runtime check failed: (g_queue_is_empty (priv->post_reload_operations))

** (evolution:8478): CRITICAL **: 07:55:17.256: void webkit_web_view_load_bytes(WebKitWebView*, GBytes*, const char*, const char*, const char*): assertion 'bytesDataSize' failed

(evolution:8478): module-webkit-editor-WARNING **: 07:55:49.082: (/build/evolution-mc96o6/evolution-3.28.1/src/modules/webkit-editor/e-webkit-editor.c:5398):webkit_editor_finalize: runtime check failed: (g_queue_is_empty (priv->post_reload_operations))

** (evolution:8478): CRITICAL **: 07:55:55.426: void webkit_web_view_load_bytes(WebKitWebView*, GBytes*, const char*, const char*, const char*): assertion 'bytesDataSize' failed

(evolution:8478): module-webkit-editor-WARNING **: 07:56:41.137: (/build/evolution-mc96o6/evolution-3.28.1/src/modules/webkit-editor/e-webkit-editor.c:5398):webkit_editor_finalize: runtime check failed: (g_queue_is_empty (priv->post_reload_operations))
Error sending IPC message: Broken pipe
Error sending IPC message: Broken pipe
Error sending IPC message: Broken pipe
Error sending IPC message: Broken pipe
Error sending IPC message: Broken pipe

---

### Post by dino99 on 2018-04-12
be sure to purge the old 16.04 settings and orphans left behind, using gtkorphan & bleachbit (as root, carefully select options)

[https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/1763419](https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/1763419)

---

