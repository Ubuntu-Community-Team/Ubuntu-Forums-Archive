---
title: "Install phpldapadmin in Lucid"
date: 2010-01-17
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by GoofYas007 on 2010-01-17
Just for someone else who might bump into it...

after installing phpldapadmin in Lucid (following this guide:
[https://help.ubuntu.com/community/InstallingphpLDAPadmin](https://help.ubuntu.com/community/InstallingphpLDAPadmin))
the page doesnt load proper.
[http://localhost/phpldapadmin](http://localhost/phpldapadmin)

It complains about:
E_STRICT: Declaration of AJAXTree::draw_dn() should be compatible with that of PLMTree::draw_dn()

Go & edit /usr/share/phpldapadmin/lib/AJAXTree.php

where it says:
class AJAXTree extends PLMTree {
        /**
draw_dn($dn,$level[COLOR="Red"]=0[/COLOR],$first_child=true,$last_child=true) {
                if (DEBUG_ENABLED)

Remove the =0 & you should be good to go.

Hope this helps. Info comes from:
[http://launchpadlibrarian.net/33328443/bug-446669.patch](http://launchpadlibrarian.net/33328443/bug-446669.patch)

---

