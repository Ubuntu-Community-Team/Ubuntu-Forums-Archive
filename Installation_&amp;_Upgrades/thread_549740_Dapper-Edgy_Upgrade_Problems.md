---
title: "Dapper-Edgy Upgrade Problems"
date: 2007-09-13
forum: Installation &amp; Upgrades
---

### Post by ashenrose on 2007-09-13
I upgraded from Daper to Edgy. Took around 10/11 hours. I had to do it via terminal (apt-get update, apt-get upgrade) as the update manager was not seeing any updates/upgrades. 

I now have Edgy and a whole bunch of issues. I will try and be systematic about it.

I have no desktop icons whatsoever and cannot get to /home or Desktop. Some other bits are not working wither, like update manager and add/remove.

I get a Gnome error message upon startup - 

[COLOR="Blue"]There was an error starting the GNOME Settings Daemon.
Some things, such as themes, sounds, or background settings may not work correctly.
The last error message was:
The name org.gnome.SettingsDaemon was not provided by any .service files
GNOME will still try to restart the Settings Daemon next time you log in.
 [/COLOR]

Bug Buddy opens soon after because nautilus won't start either.

[COLOR="Blue"]Backtrace was generated from '/usr/bin/nautilus'

(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread -1226754384 (LWP 4697)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
0xffffe410 in __kernel_vsyscall ()
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb76a334b in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb7e3a1b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
#3  <signal handler called>
#4  0xb7b8291f in gtk_menu_shell_insert () from /usr/lib/libgtk-x11-2.0.so.0
#5  0xb7c81d7a in _gtk_menu_is_empty () from /usr/lib/libgtk-x11-2.0.so.0
#6  0xb7c812b0 in _gtk_menu_is_empty () from /usr/lib/libgtk-x11-2.0.so.0
#7  0xb7c812b0 in _gtk_menu_is_empty () from /usr/lib/libgtk-x11-2.0.so.0
#8  0xb7c812b0 in _gtk_menu_is_empty () from /usr/lib/libgtk-x11-2.0.so.0
#9  0xb7c812b0 in _gtk_menu_is_empty () from /usr/lib/libgtk-x11-2.0.so.0
#10 0xb7c82218 in _gtk_menu_is_empty () from /usr/lib/libgtk-x11-2.0.so.0
#11 0xb7c82318 in gtk_ui_manager_get_ui () from /usr/lib/libgtk-x11-2.0.so.0
#12 0xb762eaa1 in g_source_is_destroyed () from /usr/lib/libglib-2.0.so.0
#13 0xb7630802 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
#14 0xb76337df in g_main_context_check () from /usr/lib/libglib-2.0.so.0
#15 0xb7633b89 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
#16 0xb7b70574 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
#17 0x08079e26 in POA_Nautilus_MetafileFactory__fini ()
#18 0xb73ed8cc in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#19 0x080672a1 in ?? ()

Thread 1 (Thread -1226754384 (LWP 4697)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb76a334b in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#2  0xb7e3a1b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
No symbol table info available.
#3  <signal handler called>
No symbol table info available.
#4  0xb7b8291f in gtk_menu_shell_insert () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#5  0xb7c81d7a in _gtk_menu_is_empty () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#6  0xb7c812b0 in _gtk_menu_is_empty () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#7  0xb7c812b0 in _gtk_menu_is_empty () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#8  0xb7c812b0 in _gtk_menu_is_empty () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#9  0xb7c812b0 in _gtk_menu_is_empty () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#10 0xb7c82218 in _gtk_menu_is_empty () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#11 0xb7c82318 in gtk_ui_manager_get_ui () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#12 0xb762eaa1 in g_source_is_destroyed () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#13 0xb7630802 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#14 0xb76337df in g_main_context_check () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#15 0xb7633b89 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#16 0xb7b70574 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#17 0x08079e26 in POA_Nautilus_MetafileFactory__fini ()
No symbol table info available.
#18 0xb73ed8cc in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#19 0x080672a1 in ?? ()
No symbol table info available.
#0  0xffffe410 in __kernel_vsyscall ()[/COLOR]

Obviously firefox works, but I can't get to the other error messages I had before I had to reboot. I have to reboot manually because none of the "Quit" Icons work either. I remember something about a "Broken Pipe"

I'm using synaptic now to download terminal.app so I have a terminal at the very least ><

I'm so confused. I've been using Ubuntu for about a year now and Dapper was doing my head in with not being able to listen to sounds (I tried every suggestion I could find) without them being seriously jerky and not being able to watch anything more than a few seconds in video/flash. I was going to upgrade straight from Edgy to Feisty, but I understand I need to sort these issues out first. 

Any help would be appreciated. I really really don't want to have to pull out my windows box again. I like a challenge, but this is beyond my skills :P

---

### Post by ashenrose on 2007-09-13
>< I can't install the terminal because add/remove won't load up.

---

### Post by rsambuca on 2007-09-13
Sorry, I am not quite sure how you upgraded.  Did you change your repositories to edgy or something?

What error occurred when you tried the recommended upgrade method first (gksu "update-manager -c")?

---

### Post by ashenrose on 2007-09-13
What error occurred when you tried the recommended upgrade method first (gksu "update-manager -c")?

The update manager appeared and said there were no updates found and there wasn't an upgrade option at the top. 

So I did the following in terminal as root.

Sudo apt-get update
Sudo apt-get distro upgrade

I am missing a step in between but I cannot find the forum where I got the tip from. It had something to do with '\dapper/\edgy' or something along those lines. Apologies for not being so clear on it. I can't access my copy-pasted notes of my exact steps.

---

### Post by rsambuca on 2007-09-13
Ahh, I think you applied a command to change your repositories in your sources.list from dapper to edgy.  I am not sure what happened here.  I'll look around for potential fixes but to be honest, it doesn't look too good.

---

### Post by ashenrose on 2007-09-13
Thank you for your help and for looking :-) I appreciate it.

I don't think I'm doing too badly, this is my first proper fudge-up of something with Linux. I have a CD burner on my windows box, so if there is absolutely no way of rescuing my poor duck-eft hybrid I will do a clean install straight to feisty. I would like to try and rescue it first though, if only for learning more about linux. The only thing that would irritate me is if firefox still needs sym-linking with its lib files in feisty too.

---

### Post by rsambuca on 2007-09-13
Can you boot into recovery mode at all?

---

### Post by ashenrose on 2007-09-13
How would I do that? I still have a normal boot up, it breaks after loging in.

---

### Post by codesplice on 2007-09-13
You can get to a recovery mode (I think) off of the install CD, or you can get to the failsafe terminal from the GRUB boot menu.

---

### Post by ashenrose on 2007-09-13
Thank you. I only have the cd for Dapper at the moment. My housemate is kindly downloading/burning Feisty for me so I can install from that if needed.

I think I might be getting somewhere with updates, I have re-installed gnome with synaptic through the broken filter, and updates appear to be trundling along. I'm not sure if it will work after them all, but I figured its worth a shot. 

If not I'll try the grub menu.

---

