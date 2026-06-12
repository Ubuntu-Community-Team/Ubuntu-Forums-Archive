---
title: "mod_speling doesn't work in Apache"
date: 2007-09-06
forum: Installation &amp; Upgrades
---

### Post by widernet_project on 2007-09-06
Hi all,
I'm trying to make apache case-insensitive in Ubuntu. I have mod_speling enabled and "CheckSpelling on" (as in this thread [http://ubuntuforums.org/showthread.php?t=342568&highlight=apache+case+insensitive](http://ubuntuforums.org/showthread.php?t=342568&highlight=apache+case+insensitive)). But it doesn't work. I tried to use a2enmod command as here [http://ubuntuforums.org/showthread.php?t=142156](http://ubuntuforums.org/showthread.php?t=142156) but it displayed error command not found (note that I compile apache 2.0.59 from the source and the folder is /usr/local/apache2. I search the folder and can't find any thing named a2enmod).
Below is my configuration file.
Any help will be more than welcome.

```

LoadModule access_module modules/mod_access.so
LoadModule auth_module modules/mod_auth.so
LoadModule auth_anon_module modules/mod_auth_anon.so
LoadModule auth_dbm_module modules/mod_auth_dbm.so
LoadModule auth_digest_module modules/mod_auth_digest.so
LoadModule ext_filter_module modules/mod_ext_filter.so
LoadModule include_module modules/mod_include.so
LoadModule log_config_module modules/mod_log_config.so
LoadModule env_module modules/mod_env.so
LoadModule expires_module modules/mod_expires.so
LoadModule headers_module modules/mod_headers.so
LoadModule setenvif_module modules/mod_setenvif.so
LoadModule mime_module modules/mod_mime.so
LoadModule dav_module modules/mod_dav.so
LoadModule status_module modules/mod_status.so
LoadModule autoindex_module modules/mod_autoindex.so
LoadModule asis_module modules/mod_asis.so
LoadModule info_module modules/mod_info.so
LoadModule cgi_module modules/mod_cgi.so
LoadModule dav_fs_module modules/mod_dav_fs.so
LoadModule vhost_alias_module modules/mod_vhost_alias.so
LoadModule negotiation_module modules/mod_negotiation.so
LoadModule dir_module modules/mod_dir.so
LoadModule imap_module modules/mod_imap.so
LoadModule actions_module modules/mod_actions.so
[COLOR="Red"]**LoadModule speling_module modules/mod_speling.so**[/COLOR]
LoadModule userdir_module modules/mod_userdir.so
LoadModule alias_module modules/mod_alias.so
LoadModule rewrite_module modules/mod_rewrite.so

LoadModule proxy_module modules/mod_proxy.so 
LoadModule proxy_connect_module modules/mod_proxy_connect.so 
LoadModule proxy_http_module modules/mod_proxy_http.so
LoadModule proxy_ftp_module modules/mod_proxy_ftp.so 

CheckSpelling on


```

---

