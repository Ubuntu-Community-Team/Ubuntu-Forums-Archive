---
title: "sudo apt-get build-dep Ubuntu Server 17.04"
date: 2017-07-26
forum: Installation &amp; Upgrades
---

### Post by danielleeson on 2017-07-26
Entered the following on command line tty1:

```
sudo apt-get build-dep libdvd-pkg libbluray-bdj libbluray-bin libbluray-dev libbluray-doc libbluray2 browser-plugin-vlc libvlc-bin libvlc-dev libvlc5 libvlccore-dev libvlccore8 phonon-backend-vlc phonon-backend-vlc-dbg phonon4qt5-backend-vlc phonon4qt5-backend-vlc-dbg vlc vlc-bin vlc-data vlc-l10n vlc-nox vlc-plugin-access-extra vlc-plugin-base vlc-plugin-notify vlc-plugin-qt vlc-plugin-qt vlc-plugin-skins2 vlc-plugin-video-output vlc-plugin-video-splitter vlc-plugin-visualization vlc-plugin-samba  gnome-mplayer mplayer mplayer-gui freeradius freeradius-common freeradius-config freeradius-dhcp freeradius-iodbc freeradius-krb5 freeradius-ldap freeradius-memcached freeradius-mysql freeradius-postgresql freeradius-utils libfreeradius-dev libfreeradius3 hostapd libauthen-simple-kerberos-perl krb5-admin-server krb5-auth-dialog krb5-config krb5-k5tls krb5-kdc krb5-locales krb5-multidev krb5-strength krb5-sync-plugin krb5-user libgssapi-krb5-2 libkrb5-26-heimdal libkrb5-3 libkrb5-dbg libkrb5support0 libpam-krb5 libpam-krb5-migrate-mit cntlm libauthen-ntlm-perl libkf5kiontlm5 libntlm0 libntlm0-dev ntlmaps python-ntlm ruby-ntlm dnss dnssec-trigger kamailio-dnssec-modules libcurl3-nss libcurl4-nss-dev libcurl4-openssl-dev libengine-pkcs11-openssl libevent-openssl-2.0-5 libghc-crypto-pubkey-openssh-dev libghc-hsopenssl-dev libghc-hsopenssl-prof libghc-hsopenssl-x509-system-dev libgnutls-openssl27 libkf5dnssd-data libkf5dnssd5 libnss-cache libnss-db libnss-docker libnss-extrausers libnss-gw-name libnss-ldap libnss-ldapd libnss-mdns libnss-myhostname libnss-mymachines libnss-mysql-bg libnss-resolve libnss-sss libnss-systemd libnss-winbind libnss-wrapper libnss3-dev libnss3-tools libsss-nss-idmap-dev libsss-nss-idmap0 libxmlsec1-nss linssid nss-passwords opendnssec opendnssec-common opendnssec-enforcer-mysql rdnssd scanssh autofs-ldap autofs5-ldap courier-authlib-ldap courier-ldap dlz-ldap-enum dovecot-ldap freeradius-ldap fts-fai-ldap fts-ltsp-ldap isc-dhcp-server-ldap krb5-kdc-ldap ldap-account-manager ldap-account-manager-lamdaemon ldap-auth-client ldap-auth-config ldap-utils ldap2dns ldap2zone ldapscripts ldaptor-utils libdbd-ldap-perl libkf5ldap-dev libkf5ldap5 libkldap4 libldap-2.4-2 libldap-common libldap2-dev libmono-ldap4.0-cil libmono-system-ldap-protocols4.0-cil libmono-system-ldap4.0-cil libmozilla-ldap-perl libnet-ldap-filterbuilder-perl libnet-ldap-perl libnet-ldap-server-perl libnet-ldap-sid-perl libnet-ldapapi-perl libnss-ldap libnss-ldapd libpam-ldap libpam-ldapd smbldap-tools sssd-ldap sudo-ldap slapd slapd-smbk5pwd cifs-utils libjcifs-java fusesmb libauthen-simple-smb-perl libauthen-smb-perl libcrypt-smbhash-perl libfilesys-smbclient-perl libsmbclient libsmbios-dev libsmbios2v5 php-smbclient python-libsmbios python-smbc python-smbpasswd python-smbus python3-smbc python3-smbus qtsmbstatus-client qtsmbstatus-language qtsmbstatus-light qtsmbstatus-server slapd-smbk5pwd smb-nat smb4k smbc smbclient smbios-utils smbldap-tools smbnetfs libwbclient-sssd libwbclient-sssd-dev puppet-module-asciiduck-sssd sssd sssd-ad sssd-ad-common sssd-common sssd-dbus sssd-krb5 sssd-krb5-common sssd-ldap sssd-proxy sssd-tools dansguardian libdansguardian-perl squid squid-cgi squid-common squid-purge squid3 squidclient squidguard squidtaild squidview libquagga-dev libquagga0 quagga quagga-bgpd quagga-core quagga-isisd quagga-ospf6d quagga-ospfd quagga-pimd quagga-ripd quagga-ripngd argonaut-samba gadmin-samba python-samba samba samba-common samba-common-bin samba-dev samba-dsdb-modules samba-libs samba-testsuite samba-vfs-modules system-config-samba vlc-plugin-samba usbip usbip-source libusbip-dev libusbip0
```


Output the following results:


```
Reading package lists... Done
Picking 'libbluray' as source package instead of 'libbluray-bdj'
Picking 'libbluray' as source package instead of 'libbluray-bin'
Picking 'libbluray' as source package instead of 'libbluray-dev'
Picking 'libbluray' as source package instead of 'libbluray-doc'
Picking 'libbluray' as source package instead of 'libbluray2'
Picking 'npapi-vlc' as source package instead of 'browser-plugin-vlc'
Picking 'vlc' as source package instead of 'libvlc-bin'
Picking 'vlc' as source package instead of 'libvlc-dev'
Picking 'vlc' as source package instead of 'libvlc5'
Picking 'vlc' as source package instead of 'libvlccore-dev'
Picking 'vlc' as source package instead of 'libvlccore8'
Picking 'phonon-backend-vlc' as source package instead of 'phonon-backend-vlc-dbg'
Picking 'phonon-backend-vlc' as source package instead of 'phonon4qt5-backend-vlc'
Picking 'phonon-backend-vlc' as source package instead of 'phonon4qt5-backend-vlc-dbg'
Picking 'vlc' as source package instead of 'vlc-bin'
Picking 'vlc' as source package instead of 'vlc-data'
Picking 'vlc' as source package instead of 'vlc-l10n'
Picking 'vlc' as source package instead of 'vlc-nox'
Picking 'vlc' as source package instead of 'vlc-plugin-access-extra'
Picking 'vlc' as source package instead of 'vlc-plugin-base'
Picking 'vlc' as source package instead of 'vlc-plugin-notify'
Picking 'vlc' as source package instead of 'vlc-plugin-qt'
Picking 'vlc' as source package instead of 'vlc-plugin-qt'
Picking 'vlc' as source package instead of 'vlc-plugin-skins2'
Picking 'vlc' as source package instead of 'vlc-plugin-video-output'
Picking 'vlc' as source package instead of 'vlc-plugin-video-splitter'
Picking 'vlc' as source package instead of 'vlc-plugin-visualization'
Picking 'vlc' as source package instead of 'vlc-plugin-samba'
Picking 'mplayer' as source package instead of 'mplayer-gui'
Picking 'freeradius' as source package instead of 'freeradius-common'
Picking 'freeradius' as source package instead of 'freeradius-config'
Picking 'freeradius' as source package instead of 'freeradius-dhcp'
Picking 'freeradius' as source package instead of 'freeradius-iodbc'
Picking 'freeradius' as source package instead of 'freeradius-krb5'
Picking 'freeradius' as source package instead of 'freeradius-ldap'
Picking 'freeradius' as source package instead of 'freeradius-memcached'
Picking 'freeradius' as source package instead of 'freeradius-mysql'
Picking 'freeradius' as source package instead of 'freeradius-postgresql'
Picking 'freeradius' as source package instead of 'freeradius-utils'
Picking 'freeradius' as source package instead of 'libfreeradius-dev'
Picking 'freeradius' as source package instead of 'libfreeradius3'
Picking 'wpa' as source package instead of 'hostapd'
Picking 'krb5' as source package instead of 'krb5-admin-server'
Picking 'kerberos-configs' as source package instead of 'krb5-config'
Picking 'krb5' as source package instead of 'krb5-k5tls'
Picking 'krb5' as source package instead of 'krb5-kdc'
Picking 'krb5' as source package instead of 'krb5-locales'
Picking 'krb5' as source package instead of 'krb5-multidev'
Picking 'krb5-sync' as source package instead of 'krb5-sync-plugin'
Picking 'krb5' as source package instead of 'krb5-user'
Picking 'krb5' as source package instead of 'libgssapi-krb5-2'
Picking 'heimdal' as source package instead of 'libkrb5-26-heimdal'
Picking 'krb5' as source package instead of 'libkrb5-3'
Picking 'krb5' as source package instead of 'libkrb5-dbg'
Picking 'krb5' as source package instead of 'libkrb5support0'
Picking 'pam-krb5-migrate' as source package instead of 'libpam-krb5-migrate-mit'
Picking 'kio' as source package instead of 'libkf5kiontlm5'
Picking 'libntlm' as source package instead of 'libntlm0'
Picking 'libntlm' as source package instead of 'libntlm0-dev'
Picking 'kamailio' as source package instead of 'kamailio-dnssec-modules'
Picking 'curl' as source package instead of 'libcurl3-nss'
Picking 'curl' as source package instead of 'libcurl4-nss-dev'
Picking 'curl' as source package instead of 'libcurl4-openssl-dev'
Picking 'libp11' as source package instead of 'libengine-pkcs11-openssl'
Picking 'libevent' as source package instead of 'libevent-openssl-2.0-5'
Picking 'haskell-crypto-pubkey-openssh' as source package instead of 'libghc-crypto-pubkey-openssh-dev'
Picking 'haskell-hsopenssl' as source package instead of 'libghc-hsopenssl-dev'
Picking 'haskell-hsopenssl' as source package instead of 'libghc-hsopenssl-prof'
Picking 'haskell-hsopenssl-x509-system' as source package instead of 'libghc-hsopenssl-x509-system-dev'
Picking 'gnutls28' as source package instead of 'libgnutls-openssl27'
Picking 'kdnssd-kf5' as source package instead of 'libkf5dnssd-data'
Picking 'kdnssd-kf5' as source package instead of 'libkf5dnssd5'
Picking 'nss-pam-ldapd' as source package instead of 'libnss-ldapd'
Picking 'nss-mdns' as source package instead of 'libnss-mdns'
Picking 'systemd' as source package instead of 'libnss-myhostname'
Picking 'systemd' as source package instead of 'libnss-mymachines'
Picking 'systemd' as source package instead of 'libnss-resolve'
Picking 'sssd' as source package instead of 'libnss-sss'
Picking 'systemd' as source package instead of 'libnss-systemd'
Picking 'samba' as source package instead of 'libnss-winbind'
Picking 'nss-wrapper' as source package instead of 'libnss-wrapper'
Picking 'nss' as source package instead of 'libnss3-dev'
Picking 'nss' as source package instead of 'libnss3-tools'
Picking 'sssd' as source package instead of 'libsss-nss-idmap-dev'
Picking 'sssd' as source package instead of 'libsss-nss-idmap0'
Picking 'xmlsec1' as source package instead of 'libxmlsec1-nss'
Picking 'opendnssec' as source package instead of 'opendnssec-common'
Picking 'opendnssec' as source package instead of 'opendnssec-enforcer-mysql'
Picking 'ndisc6' as source package instead of 'rdnssd'
Picking 'autofs' as source package instead of 'autofs-ldap'
Picking 'autofs' as source package instead of 'autofs5-ldap'
Picking 'courier-authlib' as source package instead of 'courier-authlib-ldap'
Picking 'courier' as source package instead of 'courier-ldap'
Picking 'dovecot' as source package instead of 'dovecot-ldap'
Picking 'freeradius' as source package instead of 'freeradius-ldap'
Picking 'fts' as source package instead of 'fts-fai-ldap'
Picking 'fts' as source package instead of 'fts-ltsp-ldap'
Picking 'isc-dhcp' as source package instead of 'isc-dhcp-server-ldap'
Picking 'krb5' as source package instead of 'krb5-kdc-ldap'
Picking 'ldap-account-manager' as source package instead of 'ldap-account-manager-lamdaemon'
Picking 'ldap-auth-client' as source package instead of 'ldap-auth-config'
Picking 'openldap' as source package instead of 'ldap-utils'
Picking 'ldaptor' as source package instead of 'ldaptor-utils'
Picking 'kldap' as source package instead of 'libkf5ldap-dev'
Picking 'kldap' as source package instead of 'libkf5ldap5'
Picking 'kde4pimlibs' as source package instead of 'libkldap4'
Picking 'openldap' as source package instead of 'libldap-2.4-2'
Picking 'openldap' as source package instead of 'libldap-common'
Picking 'openldap' as source package instead of 'libldap2-dev'
Picking 'mono' as source package instead of 'libmono-ldap4.0-cil'
Picking 'mono' as source package instead of 'libmono-system-ldap-protocols4.0-cil'
Picking 'mono' as source package instead of 'libmono-system-ldap4.0-cil'
Picking 'nss-pam-ldapd' as source package instead of 'libnss-ldapd'
Picking 'nss-pam-ldapd' as source package instead of 'libpam-ldapd'
Picking 'sssd' as source package instead of 'sssd-ldap'
Picking 'sudo' as source package instead of 'sudo-ldap'
Picking 'openldap' as source package instead of 'slapd'
Picking 'openldap' as source package instead of 'slapd-smbk5pwd'
Picking 'jcifs' as source package instead of 'libjcifs-java'
Picking 'samba' as source package instead of 'libsmbclient'
Picking 'libsmbios' as source package instead of 'libsmbios-dev'
Picking 'libsmbios' as source package instead of 'libsmbios2v5'
Picking 'libsmbios' as source package instead of 'python-libsmbios'
Picking 'pysmbc' as source package instead of 'python-smbc'
Picking 'i2c-tools' as source package instead of 'python-smbus'
Picking 'pysmbc' as source package instead of 'python3-smbc'
Picking 'i2c-tools' as source package instead of 'python3-smbus'
Picking 'qtsmbstatus' as source package instead of 'qtsmbstatus-client'
Picking 'qtsmbstatus' as source package instead of 'qtsmbstatus-language'
Picking 'qtsmbstatus' as source package instead of 'qtsmbstatus-light'
Picking 'qtsmbstatus' as source package instead of 'qtsmbstatus-server'
Picking 'openldap' as source package instead of 'slapd-smbk5pwd'
Picking 'nat' as source package instead of 'smb-nat'
Picking 'samba' as source package instead of 'smbclient'
Picking 'libsmbios' as source package instead of 'smbios-utils'
Picking 'sssd' as source package instead of 'libwbclient-sssd'
Picking 'sssd' as source package instead of 'libwbclient-sssd-dev'
Picking 'sssd' as source package instead of 'sssd-ad'
Picking 'sssd' as source package instead of 'sssd-ad-common'
Picking 'sssd' as source package instead of 'sssd-common'
Picking 'sssd' as source package instead of 'sssd-dbus'
Picking 'sssd' as source package instead of 'sssd-krb5'
Picking 'sssd' as source package instead of 'sssd-krb5-common'
Picking 'sssd' as source package instead of 'sssd-ldap'
Picking 'sssd' as source package instead of 'sssd-proxy'
Picking 'sssd' as source package instead of 'sssd-tools'
Picking 'squid3' as source package instead of 'squid'
Picking 'squid3' as source package instead of 'squid-cgi'
Picking 'squid3' as source package instead of 'squid-common'
Picking 'squid3' as source package instead of 'squid-purge'
Picking 'squid3' as source package instead of 'squidclient'
Picking 'quagga' as source package instead of 'libquagga-dev'
Picking 'quagga' as source package instead of 'libquagga0'
Picking 'quagga' as source package instead of 'quagga-bgpd'
Picking 'quagga' as source package instead of 'quagga-core'
Picking 'quagga' as source package instead of 'quagga-isisd'
Picking 'quagga' as source package instead of 'quagga-ospf6d'
Picking 'quagga' as source package instead of 'quagga-ospfd'
Picking 'quagga' as source package instead of 'quagga-pimd'
Picking 'quagga' as source package instead of 'quagga-ripd'
Picking 'quagga' as source package instead of 'quagga-ripngd'
Picking 'argonaut' as source package instead of 'argonaut-samba'
Picking 'samba' as source package instead of 'python-samba'
Picking 'samba' as source package instead of 'samba-common'
Picking 'samba' as source package instead of 'samba-common-bin'
Picking 'samba' as source package instead of 'samba-dev'
Picking 'samba' as source package instead of 'samba-dsdb-modules'
Picking 'samba' as source package instead of 'samba-libs'
Picking 'samba' as source package instead of 'samba-testsuite'
Picking 'samba' as source package instead of 'samba-vfs-modules'
Picking 'vlc' as source package instead of 'vlc-plugin-samba'
Picking 'usbip' as source package instead of 'usbip-source'
Picking 'usbip' as source package instead of 'libusbip-dev'
Picking 'usbip' as source package instead of 'libusbip0'
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 builddeps:autofs : Depends: libxml2-dev but it is not going to be installed
 builddeps:dlz-ldap-enum : Depends: libbind-dev but it is not going to be installed
 builddeps:dnssec-trigger : Depends: libgtk2.0-dev but it is not going to be installed
 builddeps:gadmin-samba : Depends: libgtk2.0-dev but it is not going to be installed
 builddeps:gnome-mplayer : Depends: libnautilus-extension-dev but it is not going to be installed
                           Depends: libnemo-extension-dev but it is not going to be installed
                           Depends: libgtk-3-dev but it is not going to be installed
                           Depends: libgmtk-dev (>= 1.0.7) but it is not going to be installed
                           Depends: libgpod-dev but it is not going to be installed
                           Depends: libimobiledevice-dev
                           Depends: libgda-5.0-dev but it is not going to be installed
 builddeps:kamailio : Depends: libcurl4-openssl-dev but it is not going to be installed
                      Depends: libxml2-dev but it is not going to be installed
                      Depends: unixodbc-dev but it is not going to be installed
 builddeps:kde4pimlibs : Depends: libical-dev (>= 0.42) but it is not going to be installed
                         Depends: libxslt1-dev but it is not going to be installed
 builddeps:kio : Depends: libxml2-dev but it is not going to be installed
                 Depends: libxslt1-dev but it is not going to be installed
 builddeps:krb5-auth-dialog : Depends: libglade2-dev but it is not going to be installed
                              Depends: libgtk-3-dev (>= 3.14.0) but it is not going to be installed
 builddeps:libbluray : Depends: libxml2-dev but it is not going to be installed
 builddeps:libsmbios : Depends: libxml2-dev but it is not going to be installed
 builddeps:linssid : Depends: libboost-regex-dev but it is not going to be installed
 builddeps:mono : Depends: libxslt1-dev but it is not going to be installed
 builddeps:mplayer : Depends: libass-dev but it is not going to be installed
                     Depends: libgtk2.0-dev but it is not going to be installed
 builddeps:npapi-vlc : Depends: libgtk2.0-dev but it is not going to be installed
 builddeps:opendnssec : Depends: libxml2-dev but it is not going to be installed
 builddeps:openldap : Depends: heimdal-dev but it is not going to be installed
                      Depends: unixodbc-dev but it is not going to be installed
 builddeps:squid3 : Depends: libxml2-dev but it is not going to be installed
 builddeps:sssd : Depends: libaugeas-dev but it is not going to be installed
 builddeps:vlc : Depends: libass-dev (>= 0.9.8) but it is not going to be installed
                 Depends: libgtk2.0-dev but it is not going to be installed
                 Depends: libxml2-dev but it is not going to be installed
 builddeps:xmlsec1 : Depends: libxml2-dev (>= 2.6.12) but it is not going to be installed
                     Depends: libxslt1-dev (>= 1.0.20) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
administrator@ns1:
```


I just cannot figure out why this is happening, seems to me that there is no excuse for the output I am recieving.

If anyone can help me, please do lend me a hand / voice.

Daniel

---

### Post by QIII on 2017-07-26
Hello!

Please enclose all terminal commands and their output in code tags.  This will preserve formatting (for instance:  you won't get smilies) and make your posts much easier to read.

1. If you are using the "Reply to Thread" button - highlight text and use the # button in the text box header.  Alternatively, click the # button first, place your cursor between the code tags and type or paste your text.

2. If using "Quick Reply" then type [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.  The square brackets are required.

---

### Post by oldos2er on 2017-07-26
I've never used *apt build-dep* to install dependencies for more than one source package at a time. What you're telling apt to do is to install build dependencies for all the packages in your command. Is that really what you want? If there's a particular program you're trying to compile from source, please tell us what it is.

---

