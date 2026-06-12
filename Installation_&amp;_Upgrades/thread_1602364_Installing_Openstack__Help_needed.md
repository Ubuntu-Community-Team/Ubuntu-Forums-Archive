---
title: "Installing Openstack _Help needed"
date: 2010-10-21
forum: Installation &amp; Upgrades
---

### Post by girishlc on 2010-10-21
While installing Openstack in Ubuntu Maverick, I'm stuck in below command,

euca-upload-bundle -m /tmp/kernel.manifest.xml -b mybucket

~$ euca-upload-bundle -m /tmp/kernel.manifest.xml -b mybucket
Checking bucket: mybucket
Warning: failed to parse error message from AWS: <unknown>:7:2: mismatched tag
S3ResponseError: 504 Gateway Timeout
<HTML><HEAD>
<TITLE>Network Error</TITLE>
</HEAD>
<BODY>
<FONT face="Helvetica">
<big><strong></strong></big><BR>
</FONT>
<blockquote>
<TABLE border=0 cellPadding=1 width="80%">
<TR><TD>
<FONT face="Helvetica">
<big>Network Error (gateway_error)</big>
<BR>
<BR>
</FONT>
</TD></TR>
<TR><TD>
<FONT face="Helvetica">
An error occurred attempting to communicate with an HTTP or SOCKS gateway.
</FONT>
</TD></TR>
<TR><TD>
<FONT face="Helvetica">
The gateway may be temporarily unavailable, or there could be a network problem.
</FONT>
</TD></TR>
<TR><TD>
<FONT face="Helvetica" SIZE=2>
<BR>
For assistance, contact your network support team.
</FONT>
</TD></TR>
</TABLE>
</blockquote>
</FONT>
</BODY></HTML>



Referring link [http://blog.warma.dk/2010/10/11/openstack-nova-in-](http://blog.warma.dk/2010/10/11/openstack-nova-in-)
maverick/

---

