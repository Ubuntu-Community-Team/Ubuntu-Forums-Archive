---
title: "Is it just me or does Webmin hate everyone?"
date: 2011-10-05
forum: Installation &amp; Upgrades
---

### Post by Rev. Dead Corpse on 2011-10-05
Ubuntu 11.04 running openLDAP. Trying to set up a more user friendly web interface to allow bulk administration of LDAP accounts. Looked at phpLDAPadmin and thought it was fine for large fore-brain types, but not so much for your average office worker. Webmin seems to be much more configurable to allow LDAP access to a generic user account to update Staff/Student type accounts.

After following the 11.04 server guide setup for openLDAP ([https://help.ubuntu.com/11.04/serverguide/C/openldap-server.html](https://help.ubuntu.com/11.04/serverguide/C/openldap-server.html)) I was able to use the scripts to add/remove users and groups. Again, fine for pointy headed types, not so friendly for flat skulls.

Now, enter Webmin. Follow instructions for Deb install. Add in extra packages as listed here: [http://www.webmin.com/deb.html](http://www.webmin.com/deb.html)

Ok so far. Everything looks good. I'm able to access my Db for LDAP and I can see my test user accounts. Even my SSL certs look good with the correct file paths out to /etc/ssl/blah-blah-blah.

Now we try and use Webmin to edit something. Under Global LDAP Server Option I match up my DC info and user accounts, hit Save and Viola!!!

> Failed to apply configuration : failed :

 * Stopping OpenLDAP slapd
   ...done.
 * Starting OpenLDAP slapd
   ...fail!


It blows up slapd. 

Syslog looks like this:

> Oct  5 09:09:41 ldap slapd[956]: daemon: shutdown requested and initiated.
Oct  5 09:09:41 ldap slapd[956]: slapd shutdown: waiting for 0 operations/tasks to finish
Oct  5 09:09:41 ldap slapd[956]: bdb(dc=nodomain): PANIC: fatal region error detected; run recovery
Oct  5 09:09:41 ldap slapd[956]: last message repeated 3 times
Oct  5 09:09:41 ldap slapd[956]: bdb_db_close: database "dc=nodomain": txn_checkpoint failed: DB_RUNRECOVERY: Fatal error, run database recovery (-30974).
Oct  5 09:09:41 ldap slapd[956]: bdb(dc=nodomain): File handles still open at environment close
Oct  5 09:09:41 ldap slapd[956]: bdb(dc=nodomain): Open file handle: /var/lib/ldap/id2entry.bdb
Oct  5 09:09:41 ldap slapd[956]: bdb(dc=nodomain): Open file handle: /var/lib/ldap/dn2id.bdb
Oct  5 09:09:41 ldap slapd[956]: bdb(dc=nodomain): PANIC: fatal region error detected; run recovery
Oct  5 09:09:41 ldap slapd[956]: bdb_db_close: database "dc=nodomain": close failed: DB_RUNRECOVERY: Fatal error, run database recovery (-30974)
Oct  5 09:09:41 ldap slapd[956]: slapd stopped.
Oct  5 09:09:41 ldap slapd[2824]: @(#) $OpenLDAP: slapd 2.4.23 (Apr  7 2011 18:00:55) $#012#011buildd@allspice:/build/buildd/openldap-2.4.23/debian/build/servers/slapd
Oct  5 09:09:41 ldap slapd[2824]: olcSuffix: value #0: <olcSuffix> namingContext "dc=biglake,dc=k12,dc=mn,dc=us" already served by a preceding hdb database serving namingContext "dc=biglake,dc=k12,dc=mn,dc=us"
Oct  5 09:09:41 ldap slapd[2824]: config error processing olcDatabase={2}hdb,cn=config: <olcSuffix> namingContext "dc=biglake,dc=k12,dc=mn,dc=us" already served by a preceding hdb database
Oct  5 09:09:41 ldap slapd[2824]: slapd stopped.
Oct  5 09:09:41 ldap slapd[2824]: connections_destroy: nothing to destroy.
Oct  5 09:09:45 ldap slapd[2831]: @(#) $OpenLDAP: slapd 2.4.23 (Apr  7 2011 18:00:55) $#012#011buildd@allspice:/build/buildd/openldap-2.4.23/debian/build/servers/slapd
Oct  5 09:10:30 ldap slapd[2918]: @(#) $OpenLDAP: slapd 2.4.23 (Apr  7 2011 18:00:55) $#012#011buildd@allspice:/build/buildd/openldap-2.4.23/debian/build/servers/slapd
Oct  5 09:10:30 ldap slapd[2918]: olcSuffix: value #0: <olcSuffix> namingContext "dc=biglake,dc=k12,dc=mn,dc=us" already served by a preceding hdb database serving namingContext "dc=biglake,dc=k12,dc=mn,dc=us"
Oct  5 09:10:30 ldap slapd[2918]: config error processing olcDatabase={2}hdb,cn=config: <olcSuffix> namingContext "dc=biglake,dc=k12,dc=mn,dc=us" already served by a preceding hdb database
Oct  5 09:10:30 ldap slapd[2918]: slapd stopped.
Oct  5 09:10:30 ldap slapd[2918]: connections_destroy: nothing to destroy.

Any ideas on what I'm doing wrong?

---

### Post by houstonbofh on 2012-05-25
I know this is old, and by now you have either fixed it, or just shot the darn thing.  (I would shoot mine, but it is a VM...  Hard to shoot those)

I have been working on a corrupt LDAP install and finding links to tools that no longer exist, and other frustrations...

And your subject was the first thing that made me smile all day!:lolflag:

So, yes.  Webmin hates everyone, and LDAP is a sadist.

And for me, it looks like the fix is to blow it all away and reinstall from scratch.  At least that is easy on a vm...

---

