---
title: "Ejabberd XML-RPC server Nightmare :("
date: 2011-07-14
forum: Installation &amp; Upgrades
---

### Post by markdoogie on 2011-07-14
Hi all, 

I am Network admin but new at Linux, 
Its been a Week i am trying to Install and get  XML-RPC to work on Ejabberd.
Ejabberd worked fine till i Tried to install XML-RPC
Since i added {mod_xmlrpc,      []}, into the Ejabberd.cfg
and i restart it.. It looks like it crashes it.
The reason why i think that is because there are no updates in the Ejabberd log file Until i Reboot the server.
Here is the last entry in the log:

=ERROR REPORT==== 2011-07-14 12:48:44 ===
E(<0.38.0>:ejabberd_listener:272) : Error starting the ejabberd listener: ejabberd_xmlrpc.
It could not be loaded or is not an ejabberd listener.
Error: {{'EXIT',{undef,[{ejabberd_xmlrpc,socket_type,[]},
                        {ejabberd_listener,start,3},
                        {supervisor,do_start_child,2},
                        {supervisor,handle_start_child,2},
                        {supervisor,handle_call,3},
                        {gen_server,handle_msg,5},
                        {proc_lib,init_p_do_apply,3}]}},
        {child,undefined,
               {4560,{0,0,0,0},tcp},
               {ejabberd_listener,start,
                                  [{4560,{0,0,0,0},tcp},ejabberd_xmlrpc,[]]},
               transient,brutal_kill,worker,
               [ejabberd_listener]}}

---

### Post by pjhile on 2012-07-07
I seem to be having the problem.  I'll let you know if I stumble across the answer.

---

