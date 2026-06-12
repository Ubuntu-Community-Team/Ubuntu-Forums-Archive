---
title: "[SOLVED] apache won't load after upgrade - modules no longer exist? how to load?"
date: 2008-10-25
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by jetpeach on 2008-10-25
After upgraded, it seems perhaps some modules aren't loaded into my apache2 server anymore, although I don't know for sure this is the problem. Basically, when trying to start apache
"sudo apache2ctl restart" or the inet.d thing
I get
[I]Syntax error on line 112 of /etc/apache2/apache2.conf:
Invalid command 'Order', perhaps misspelled or defined by a module not included in the server configuration[/I]
The problem area in the apache2.conf is:
<Files ~ "^\.ht">
    Order allow,deny
    Deny from all
</Files>
but this worked fine before. Anyway, I commented it out for now, but then I get
[I]Syntax error on line 1 of /etc/apache2/conf.d/apache2-doc:
Invalid command 'Alias', perhaps misspelled or defined by a module not included in the server configuration[/I]
In this file the problem line is:
Alias /manual /usr/share/doc/apache2-doc/manual/

So I begin thinking, it must be a problem with modules that are no longer loaded automatically in Intrepid. But how do I load these again? Where? Any help would be greatly appreciated.

jet


To help Debug:
*apache2ctl -l* output is:
Compiled in modules:
  core.c
  mod_log_config.c
  mod_logio.c
  prefork.c
  http_core.c
  mod_so.c

Inside the folder *mods-enabled* are the files:
alias.conf       authz_default.load    autoindex.conf  dir.load   negotiation.conf  setenvif.conf
alias.load       authz_groupfile.load  autoindex.load  env.load   negotiation.load  setenvif.load
auth_basic.load  authz_host.load       cgi.load        mime.conf  php5.conf         status.conf
authn_file.load  authz_user.load       dir.conf        mime.load  php5.load         status.load

---

### Post by jetpeach on 2008-10-27
Problem solved: Not sure how/why, but during the upgrade my apache2.conf got edited badly and these lines were missing:
# Include module configuration:
Include /etc/apache2/mods-enabled/*.load
Include /etc/apache2/mods-enabled/*.conf

they're pretty critical too!
i think it happened when i was merging code from the old file to the new file.... copied and pasted on top of some junk... oops!

---

