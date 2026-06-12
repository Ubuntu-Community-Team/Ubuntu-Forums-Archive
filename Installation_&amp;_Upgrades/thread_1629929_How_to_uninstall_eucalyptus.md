---
title: "How to uninstall eucalyptus"
date: 2010-11-24
forum: Installation &amp; Upgrades
---

### Post by x17y19 on 2010-11-24
Hi,

After installing and then uninstalling the various eucalyptus
packages, I find that the following files are still present;
can I just manually remove all these files (don't know if that
might break something).

Thanks for any help.

The file list and the output of 'dpkg -l' is shown below:

/etc/eucalyptus/axis2
/etc/eucalyptus/cloud.d
/etc/eucalyptus/eucalyptus-cc.conf
/etc/eucalyptus/eucalyptus-ipaddr.conf
/etc/eucalyptus/eucalyptus-nc.conf
/etc/eucalyptus/eucalyptus-sc.conf
/etc/eucalyptus/eucalyptus-version
/etc/eucalyptus/eucalyptus.conf
/etc/eucalyptus/eucalyptus.local.conf
/etc/eucalyptus/eucalyptus.local.conf.bak
/etc/eucalyptus/httpd.conf
/etc/eucalyptus/vtunall.conf.template
/etc/eucalyptus/wrappers.conf
/etc/eucalyptus/axis2/axis2.xml
/etc/eucalyptus/cloud.d/eucalyptus-web-default.properties
/etc/eucalyptus/cloud.d/eucalyptus-web.properties
/etc/eucalyptus/cloud.d/gwt-web.xml
/etc/eucalyptus/cloud.d/security.policy
/etc/eucalyptus/cloud.d/www
/etc/eucalyptus/cloud.d/www/admin.xml
/etc/eucalyptus/cloud.d/www/preseed.xml

/etc/init/eucalyptus-cc-publication.conf                        eucalyptus-cc
/etc/init/eucalyptus-cc.conf                                    eucalyptus-cc
/etc/init/eucalyptus-cloud-publication.conf
/etc/init/eucalyptus-cloud.conf
/etc/init/eucalyptus-nc-publication.conf                        eucalyptus-nc
/etc/init/eucalyptus-nc.conf                                    eucalyptus-nc
/etc/init/eucalyptus-network.conf
/etc/init/eucalyptus-sc-publication.conf                        eucalyptus-sc
/etc/init/eucalyptus-sc.conf                                    eucalyptus-sc
/etc/init/eucalyptus-walrus-publication.conf
/etc/init/eucalyptus-walrus.conf
/etc/init/eucalyptus.conf

/etc/sysctl.d/30-eucalyptus-nc.conf                             eucalyptus-nc

/etc/update-motd.d/15-eucalyptus-url

/var/lib/eucalyptus

/var/lib/dpkg/info/eucalyptus-cc.list
/var/lib/dpkg/info/eucalyptus-cc.postrm
/var/lib/dpkg/info/eucalyptus-cloud.list
/var/lib/dpkg/info/eucalyptus-cloud.postrm
/var/lib/dpkg/info/eucalyptus-common.list
/var/lib/dpkg/info/eucalyptus-common.postrm
/var/lib/dpkg/info/eucalyptus-java-common.list
/var/lib/dpkg/info/eucalyptus-nc.list
/var/lib/dpkg/info/eucalyptus-nc.postrm
/var/lib/dpkg/info/eucalyptus-sc.list
/var/lib/dpkg/info/eucalyptus-sc.postrm
/var/lib/dpkg/info/eucalyptus-walrus.list
/var/lib/dpkg/info/eucalyptus-walrus.postrm

/var/lib/eucalyptus/.ssh
/var/lib/eucalyptus/bukkits
/var/lib/eucalyptus/nodes.list
/var/lib/eucalyptus/volumes
/var/lib/eucalyptus/.ssh/authorized_keys
/var/lib/eucalyptus/.ssh/id_rsa
/var/lib/eucalyptus/.ssh/id_rsa.pub

/var/lib/image-store-proxy/eucalyptus
/var/lib/update-rc.d/eucalyptus
/var/lib/update-rc.d/eucalyptus-cc
/var/lib/update-rc.d/eucalyptus-cc-publication
/var/lib/update-rc.d/eucalyptus-cloud
/var/lib/update-rc.d/eucalyptus-cloud-publication
/var/lib/update-rc.d/eucalyptus-nc
/var/lib/update-rc.d/eucalyptus-nc-publication
/var/lib/update-rc.d/eucalyptus-network
/var/lib/update-rc.d/eucalyptus-sc
/var/lib/update-rc.d/eucalyptus-sc-publication
/var/lib/update-rc.d/eucalyptus-walrus
/var/lib/update-rc.d/eucalyptus-walrus-publication

/var/log/eucalyptus
/var/log/eucalyptus/axis2c.log
/var/log/eucalyptus/euca_test_nc.log
/var/log/eucalyptus/httpd-cc_error_log
/var/log/eucalyptus/httpd-nc_error_log
/var/log/eucalyptus/registration.log

dpkg shows the following:

dpkg -l 'eucalyptus*'
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name            Version         Description
+++-===============-===============-==============================================
un  eucalyptus-cc   <none>          (no description available)
rc  eucalyptus-clou 1.6.2-0ubuntu30 Elastic Utility Computing Architecture - Cloud
rc  eucalyptus-comm 1.6.2-0ubuntu30 Elastic Utility Computing Architecture - Commo
un  eucalyptus-gl   <none>          (no description available)
rc  eucalyptus-java 1.6.2-0ubuntu30 Elastic Utility Computing Architecture - Commo
un  eucalyptus-java <none>          (no description available)
un  eucalyptus-nc   <none>          (no description available)
un  eucalyptus-sc   <none>          (no description available)
rc  eucalyptus-walr 1.6.2-0ubuntu30 Elastic Utility Computing Architecture - Walru

---

