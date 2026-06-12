---
title: "trying to setup proftpd but getting into problems (permissions)"
date: 2011-04-20
forum: Installation &amp; Upgrades
---

### Post by npereira on 2011-04-20
Hi all,

I really need help, i looked through the docs but can seem to figure it out.

I setup proftpd and configured to only have access to /var/www

both users cannot upload, create or delete files or directory.

Here is my proftpd config:

Include /etc/proftpd/modules.conf
UseIPv6                on
IdentLookups            off
ServerName            "Debian"
ServerType            standalone
DeferWelcome            off
MultilineRFC2228        on
DefaultServer            on
ShowSymlinks            on
TimeoutNoTransfer        600
TimeoutStalled            600
TimeoutIdle            1200
DisplayLogin                    welcome.msg
DisplayChdir                   .message true
ListOptions                    "-l"
DenyFilter            \*.*/
Port                21
<IfModule mod_dynmasq.c>
</IfModule>
MaxInstances            30
User                proftpd
Group                nogroup
Umask                022  022
AllowOverwrite            on
TransferLog /var/log/proftpd/xferlog
SystemLog   /var/log/proftpd/proftpd.log
<IfModule mod_quotatab.c>
QuotaEngine off
</IfModule>
<IfModule mod_ratio.c>
Ratios off
</IfModule>
<IfModule mod_delay.c>
DelayEngine on
</IfModule>
<IfModule mod_ctrls.c>
ControlsEngine        off
ControlsMaxClients    2
ControlsLog           /var/log/proftpd/controls.log
ControlsInterval      5
ControlsSocket        /var/run/proftpd/proftpd.sock
</IfModule>
<IfModule mod_ctrls_admin.c>
AdminControlsEngine off
</IfModule>
<Global>
  <Limit ALL>
  </Limit>
DefaultRoot /var/www nelson
DefaultRoot /var/www mattir
ShowSymlinks on
</Global>

---

