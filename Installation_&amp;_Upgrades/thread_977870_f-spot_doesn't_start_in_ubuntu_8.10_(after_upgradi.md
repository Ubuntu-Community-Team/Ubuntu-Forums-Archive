---
title: "f-spot doesn't start in ubuntu 8.10 (after upgrading from 8.04)"
date: 2008-11-10
forum: Installation &amp; Upgrades
---

### Post by Magic_Spehar on 2008-11-10
Here's what it says in the terminal:

~$ f-spot
[Info  21:52:04.141] Initializing DBus
[Info  21:52:04.258] Initializing Mono.Addins
[Info  21:52:04.445] Starting new FSpot server

(f-spot:7888): Gtk-CRITICAL **: gtk_window_resize: assertion `width > 0' failed
The program 'f-spot' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadRequest (invalid request code or no such operation)'.
  (Details: serial 327 error_code 1 request_code 143 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

---

### Post by directhex on 2008-11-10
Please pastebin the result of "gconftool-2 -a /apps/f-spot/ui"

---

### Post by Magic_Spehar on 2008-11-10
> **directhex said:**
> Please pastebin the result of "gconftool-2 -a /apps/f-spot/ui"


Here it is Directhex:

group_adaptor_sort_asc = false
 viewer_width = 640
 show_filmstrip = true
 show_toolbar = true
 import_window_width = 0
 show_sidebar = true
 sidebar_size = 200
 expanded_tags = []
 zoom = 0.3333333432674408
 tag_icon_size = 48
 show_ratings = true
 group_adaptor = 0
 viewer_show_filenames = true
 viewer_maximized = false
 glass_position = 95
 viewer_show_toolbar = true
 show_tags = true
 import_window_pane_position = 0
 maximized = true
 show_dates = true
 show_timeline = true
 viewer_height = 480

---

### Post by directhex on 2008-11-10
That's all of it? Odd, but you seem to be missing some values. Try running gconf-editor, go to /apps/f-spot/ui, and create 4 new integer keys:

 main_window_x = 673
 main_window_y = 643
 main_window_width = 624
 main_window_height = 433

---

### Post by Magic_Spehar on 2008-11-10
I created the keys but F-spot still doesn't start. 

Now the output is: 

group_adaptor_sort_asc = false
 viewer_width = 640
 main_window_width = 624
 show_filmstrip = true
 show_toolbar = true
 import_window_width = 0
 show_sidebar = true
 sidebar_size = 200
 expanded_tags = []
 zoom = 0.3333333432674408
 tag_icon_size = 48
 show_ratings = true
 group_adaptor = 0
 viewer_show_filenames = true
 viewer_maximized = false
 glass_position = 95
 main_window_x = 673
 viewer_show_toolbar = true
 main_window_y = 643
 main_window_height = 433
 show_tags = true
 import_window_pane_position = 0
 maximized = true
 show_dates = true
 show_timeline = true
 viewer_height = 480

---

### Post by directhex on 2008-11-10
Same error?

---

### Post by Magic_Spehar on 2008-11-11
> **directhex said:**
> Same error?
yes.  F-spot tries to start.  For a second you get a splash screen and then it disappears.

---

### Post by Quarkrad on 2008-11-11
I have the same problem as the first post.  In my case when I type:

gconftool-2 -a /apps/f-spot/ui

I only get one line of text back -all it says is:

tag_icon_size = 24


I have un installed and reinstalled but no change surely this is not an isolated case - there must be a fix

---

### Post by PaaniC on 2008-11-18
Hi,

i have the same error too.:(

Here is my output of gconf

$ gconftool-2 -a /apps/f-spot/ui
 group_adaptor_sort_asc = true
 show_filmstrip = true
 show_toolbar = true
 import_window_width = 640
 show_sidebar = true
 sidebar_size = 200
 expanded_tags = [6]
 zoom = 0.3333333432674408
 tag_icon_size = 48
 group_adaptor = 1
 show_ratings = true
 import_window_height = 443
 glass_position = 0
 show_tags = true
 import_window_pane_position = 400
 maximized = true
 show_dates = true
 show_timeline = true

kr
PaaniC

---

### Post by riban on 2008-11-20
I have the same problem with result of gconftool-2 -a /apps/f-spot/ui:

  tag_icon_size = 24

This is on a fresh install of Ubuntu 8.10 on AMD Athlon 32bit host.

---

### Post by Magic_Spehar on 2008-11-24
The initial problem is resolved (by itself).  Today I tried f-spot in the terminal and f-spot starts normally again.  
I guess there has probably been an update of one of the depencies for f-spot lately.

---

