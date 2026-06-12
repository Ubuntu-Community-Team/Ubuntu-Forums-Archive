---
title: "mailgraph and amavis-stats"
date: 2005-10-15
forum: Installation &amp; Upgrades
---

### Post by njclark on 2005-10-15
Hi,


I've set-up an email gateway with postfix+amavis+clamav+spamassissin using Ubuntu 5.10.  Everything's fine.

When I try to get some nice graphical reports using mailgraph and amavis-stats I can't seem to get any graphs coming out.

under amavis-stats..  I get the following error

amavis-stats::error: rrd_graph(): 1
amavis-stats::error: rrd_graph(): 1

and on mailgraph, I get this error:

[Sun Oct 16 07:22:11 2005] [error]  COMMENT:[Sun Oct 16 07:22:11 2005]\\l, referer: [http://XXXXXX/cgi-bin/mailgraph.cgi](http://XXXXXX/cgi-bin/mailgraph.cgi)
[Sun Oct 16 07:22:11 2005] [error] Premature end of script headers: mailgraph.cgi, referer: [http://XXXXXX/cgi-bin/mailgraph.cgi](http://XXXXXX/cgi-bin/mailgraph.cgi)
[Sun Oct 16 07:22:11 2005] [error] ERROR: Garbage ':22:11 2005]\\l' after command:, referer: [http://XXXXXX/cgi-bin/mailgraph.cgi](http://XXXXXX/cgi-bin/mailgraph.cgi)

Any assistance would be greatly appreciated.


Cheers,


John Clark

---

### Post by cllsr on 2006-01-31
Has this ever been fixed?

 I did some googling and there seem to be alot of problems with this version. 

I have it working on a hoary install and all the files seem to be identical.

Just curious,

---

### Post by seppe on 2006-05-25
I solved this bug by removing the 'COMMENT:' lines (81 and 151) in [FONT="monospace"]/usr/lib/cgi-bin/mailgraph.cgi[/FONT]. It works for me (Ubuntu Breezy Badger 5.10, mailgraph 1.10 installed with apt-get).

I found this solution on [mailgraph mailinglist archive]("http://lists.ee.ethz.ch/mailgraph/").

P.S: I also tried the new [1.12 version]("http://people.ee.ethz.ch/~dws/software/mailgraph/pub/mailgraph-1.12.tar.gz") (I simply changed the .cgi file with the new one): with the new release this problem seems solved.

---

