---
title: "Apache2 Will Not Start Error"
date: 2011-03-27
forum: Installation &amp; Upgrades
---

### Post by chuck.b on 2011-03-27
Noticed that my site was down, tried to start Apache2 and got the following error

```
Syntax error on line 160 of /etc/apache2/apache2.conf:
Invalid command 'Order', perhaps misspelled or defined by a module not included in the server configuration
Action 'configtest' failed.
The Apache error log may have more information.
   ...fail!

```Contents of /etc/apache2/apache2.conf around line 160

```

<Files ~ "^\.ht">
    Order allow,deny
    Deny from all
    Satisfy all
</Files>

```This points to authz_host.load, other posts said to make sure that it is there and here is a list of the contents of my /etc/apache2/mods-enabled 

```
alias.conf            dav_fs.conf   negotiation.conf  ruby.load
alias.load            dav_fs.load   negotiation.load  setenvif.conf
auth_basic.load       dav.load      php5.conf         setenvif.load
authn_file.load       deflate.conf  php5.load         ssl.conf
authz_default.load    deflate.load  proxy.conf        ssl.load
authz_groupfile.load  dir.conf      proxy_http.load   status.conf
authz_host.load       dir.load      proxy.load        status.load
authz_user.load       env.load      python.load       suexec.load
autoindex.conf        include.load  reqtimeout.conf
autoindex.load        mime.conf     reqtimeout.load
cgi.load              mime.load     rewrite.load

```and a cat of the authz_host.load

```
LoadModule authz_host_module /usr/lib/apache2/modules/mod_authz_host.so

```Following that to the next location ls /usr/lib/apache2/modules indicates that mod_authz_host.so is there

```
httpd.exp               mod_cgi.so           mod_mime.so
libphp5.so              mod_charset_lite.so  mod_negotiation.so
mod_actions.so          mod_dav_fs.so        mod_proxy_ajp.so
mod_alias.so            mod_dav_lock.so      mod_proxy_balancer.so
mod_asis.so             mod_dav.so           mod_proxy_connect.so
mod_auth_basic.so       mod_dbd.so           mod_proxy_ftp.so
mod_auth_digest.so      mod_deflate.so       mod_proxy_http.so
mod_authn_alias.so      mod_dir.so           mod_proxy_scgi.so
mod_authn_anon.so       mod_disk_cache.so    mod_proxy.so
mod_authn_dbd.so        mod_dumpio.so        mod_python.so
mod_authn_dbm.so        mod_env.so           mod_reqtimeout.so
mod_authn_default.so    mod_expires.so       mod_rewrite.so
mod_authn_file.so       mod_ext_filter.so    mod_ruby.so
mod_authnz_ldap.so      mod_file_cache.so    mod_setenvif.so
mod_authz_dbm.so        mod_filter.so        mod_speling.so
mod_authz_default.so    mod_headers.so       mod_ssl.so
mod_authz_groupfile.so  mod_ident.so         mod_status.so
mod_authz_host.so       mod_imagemap.so      mod_substitute.so
mod_authz_owner.so      mod_include.so       mod_suexec.so
mod_authz_user.so       mod_info.so          mod_unique_id.so
mod_autoindex.so        mod_ldap.so          mod_userdir.so
mod_cache.so            mod_log_forensic.so  mod_usertrack.so
mod_cern_meta.so        mod_mem_cache.so     mod_version.so
mod_cgid.so             mod_mime_magic.so    mod_vhost_alias.so

```Although the contests of that file does not look like much, a bunch of @ and what not. 

Need some help trying to get my site back up and running. I have tried to removed and install Apache2 again and again, following a previous post by trying 

```
sudo aptitude purge apache2-common
sudo aptitude install apache2

```With no luck.

---

