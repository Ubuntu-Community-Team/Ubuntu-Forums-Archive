---
title: "Ebox Users and group module error"
date: 2011-09-13
forum: Installation &amp; Upgrades
---

### Post by pikkiem on 2011-09-13
I am trying to configure the users and groups module in ubuntu server 10.04LTS via ebox, but a nasty error occurs. This is the error message:
A really nasty bug has occurred
Exception
Failed to enable: root command ldapadd -H 'ldapi://' -Y EXTERNAL -c -f /var/lib/ebox/tmp/slapd-master.ldif failed. Error output: ldap_sasl_interactive_bind_s: Can't contact LDAP server (-1) Command output: . Exit value: 255
Trace
Failed to enable: root command ldapadd -H 'ldapi://' -Y EXTERNAL -c -f /var/lib/ebox/tmp/slapd-master.ldif failed.
Error output: ldap_sasl_interactive_bind_s: Can't contact LDAP server (-1)

Command output: .
Exit value: 255 at /usr/share/perl5/EBox/CGI/ServiceModule/ConfigureModuleController.pm line 74
EBox::CGI::ServiceModule::ConfigureModuleController::_process('EBox::CGI::ServiceModule::ConfigureModuleController=HASH(0x7f...') called at /usr/share/perl5/EBox/CGI/Base.pm line 262
EBox::CGI::Base::run('EBox::CGI::ServiceModule::ConfigureModuleController=HASH(0x7f...') called at /usr/share/perl5/EBox/CGI/Run.pm line 120
EBox::CGI::Run::run('EBox::CGI::Run', 'ServiceModule/ConfigureModuleController', 'EBox') called at /usr/share/ebox/cgi/ebox.cgi line 19
ModPerl::ROOT::ModPerl::Registry::usr_share_ebox_cgi_ebox_2ecgi::handler('Apache2::RequestRec=SCALAR(0x7ff4d9144e48)') called at /usr/lib/perl5/ModPerl/RegistryCooker.pm line 204
eval {...} called at /usr/lib/perl5/ModPerl/RegistryCooker.pm line 204
ModPerl::RegistryCooker::run('ModPerl::Registry=HASH(0x7ff4d64966d8)') called at /usr/lib/perl5/ModPerl/RegistryCooker.pm line 170
ModPerl::RegistryCooker::default_handler('ModPerl::Registry=HASH(0x7ff4d64966d8)') called at /usr/lib/perl5/ModPerl/Registry.pm line 31
ModPerl::Registry::handler('ModPerl::Registry', 'Apache2::RequestRec=SCALAR(0x7ff4d9144e48)') called at -e line 0
eval {...} called at -e line 0

I have a little too little knowledge to know what the problem is and would like to ask for some assistance to correct this problem. I am running the 64bit version of the server package.

Can anyone assist me?

---

### Post by kheston on 2011-10-01
I'm having the same issue.  Anyone know a fix?

---

