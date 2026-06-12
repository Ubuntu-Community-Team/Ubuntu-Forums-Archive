---
title: "Unable to upgrade or install programs becasue of broken WINE mono dependencies"
date: 2023-10-27
forum: Installation &amp; Upgrades
---

### Post by ryankm on 2023-10-27
There was an error when trying to install mono-complete and now I am stuck like this.
[ATTACH]292960[/ATTACH]
```
[FONT=monospace][COLOR=#000000] sudo apt upgrade [/COLOR]
Reading package lists... Done 
Building dependency tree... Done 
Reading state information... Done 
You might want to run 'apt --fix-broken install' to correct these. 
The following packages have unmet dependencies: 
 mono-complete : Depends: mono-devel (= 6.8.0.105+dfsg-3.3) but it is not installed 
 mono-xsp4-base : Depends: mono-devel but it is not installed 
[COLOR=#ff5454]**E: **[/COLOR][COLOR=#000000]Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).[/COLOR]

[/FONT]
```

```
[FONT=monospace][COLOR=#54ff54]**ryanm@ryan-GLBWR-RRRSSSCCC**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ sudo apt --fix-broken install [/COLOR]
Reading package lists... Done 
Building dependency tree... Done 
Reading state information... Done 
Correcting dependencies... Done 
The following additional packages will be installed: 
  mono-devel 
The following NEW packages will be installed: 
  mono-devel 
0 upgraded, 1 newly installed, 0 to remove and 83 not upgraded. 
173 not fully installed or removed. 
Need to get 0 B/28.6 MB of archives. 
After this operation, 119 MB of additional disk space will be used. 
Do you want to continue? [Y/n] y 
(Reading database ... 490336 files and directories currently installed.) 
Preparing to unpack .../mono-devel_6.8.0.105+dfsg-3.3_all.deb ... 
Unpacking mono-devel (6.8.0.105+dfsg-3.3) ... 
[COLOR=#000000]**dpkg:**[/COLOR][COLOR=#000000] error processing archive /var/cache/apt/archives/mono-devel_6.8.0.105+dfsg-3.3_all.deb (--unpack): [/COLOR]
 trying to overwrite '/usr/bin/disco', which is also in package discodos 1.0~rc2-2 
[COLOR=#000000]**dpkg-deb:**[/COLOR][COLOR=#000000] [/COLOR][COLOR=#ff5454]**error:**[/COLOR][COLOR=#000000] paste subprocess was killed by signal (Broken pipe) [/COLOR]
Errors were encountered while processing: 
 /var/cache/apt/archives/mono-devel_6.8.0.105+dfsg-3.3_all.deb 
[COLOR=#ff5454]**E: **[/COLOR][COLOR=#000000]Sub-process /usr/bin/dpkg returned an error code (1)[/COLOR]


[/FONT]
```
```
[FONT=monospace][COLOR=#54ff54]**ryanm@ryan-GLBWR-RRRSSSCCC**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ sudo sudo dpkg --remove --force-remove-reinstreq mono-complete [/COLOR]
(Reading database ... 490336 files and directories currently installed.) 
Removing mono-complete (6.8.0.105+dfsg-3.3) ...

[/FONT]
```
```
[FONT=monospace][COLOR=#54ff54]**ryanm@ryan-GLBWR-RRRSSSCCC**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ sudo apt upgrade [/COLOR]
Reading package lists... Done 
Building dependency tree... Done 
Reading state information... Done 
You might want to run 'apt --fix-broken install' to correct these. 
The following packages have unmet dependencies: 
 mono-xsp4-base : Depends: mono-devel but it is not installed 
[COLOR=#ff5454]**E: **[/COLOR][COLOR=#000000]Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution). [/COLOR]
[COLOR=#54ff54]**ryanm@ryan-GLBWR-RRRSSSCCC**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ sudo sudo dpkg --remove --force-remove-reinstreq mono-devel [/COLOR]
[COLOR=#000000]**dpkg:**[/COLOR][COLOR=#000000] [/COLOR][COLOR=#ffff54]**warning:**[/COLOR][COLOR=#000000] ignoring request to remove mono-devel which isn't installed [/COLOR]
[COLOR=#54ff54]**ryanm@ryan-GLBWR-RRRSSSCCC**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ sudo sudo dpkg --remove --force-remove-reinstreq mono-xsp4-base [/COLOR]
[COLOR=#000000]**dpkg:**[/COLOR][COLOR=#000000] dependency problems prevent removal of mono-xsp4-base: [/COLOR]
 mono-xsp4 depends on mono-xsp4-base (= 4.2-2.4). 

[COLOR=#000000]**dpkg:**[/COLOR][COLOR=#000000] error processing package mono-xsp4-base (--remove): [/COLOR]
 dependency problems - not removing 
Errors were encountered while processing: 
 mono-xsp4-base

[/FONT]
```
```
[FONT=monospace][COLOR=#54ff54]**ryanm@ryan-GLBWR-RRRSSSCCC**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ sudo sudo dpkg --remove --force-remove-reinstreq mono-xsp4 [/COLOR]
[COLOR=#000000]**dpkg:**[/COLOR][COLOR=#000000] dependency problems prevent removal of mono-xsp4: [/COLOR]
 monodoc-http depends on mono-xsp4 | mono-apache-server4 | mono-fastcgi-server4; however: 
  Package mono-xsp4 is to be removed. 
  Package mono-apache-server4 is not installed. 
  Package mono-fastcgi-server4 is not installed. 

[COLOR=#000000]**dpkg:**[/COLOR][COLOR=#000000] error processing package mono-xsp4 (--remove): [/COLOR]
 dependency problems - not removing 
Errors were encountered while processing: 
 mono-xsp4

[/FONT]
```
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=292961&stc=1[/IMG]
What do i do so I can keep updating....

I made a little headway removing mono-complete which was the original program apt installed that caused the problem do to a broken pipe issue when trying to install mono-complete via apt last week.  Anyway I'd like to completely remove this for now.  I don't need wine mono right now for what I am trying to do.

---

### Post by ryankm on 2023-10-27
```
[FONT=monospace][COLOR=#54ff54]**ryanm@ryan-GLBWR-RRRSSSCCC**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$  sudo apt-get install -f [/COLOR]
Reading package lists... Done 
Building dependency tree... Done 
Reading state information... Done 
Correcting dependencies... Done 
The following packages were automatically installed and are no longer required: 
  ca-certificates-mono cli-common libgdiplus libjs-xmlextras libmono-2.0-1 libmono-2.0-dev 
  libmono-accessibility4.0-cil libmono-btls-interface4.0-cil libmono-cairo4.0-cil libmono-cecil-private-cil 
  libmono-cil-dev libmono-codecontracts4.0-cil libmono-compilerservices-symbolwriter4.0-cil 
  libmono-corlib4.5-cil libmono-corlib4.5-dll libmono-cscompmgd0.0-cil libmono-csharp4.0c-cil 
  libmono-custommarshalers4.0-cil libmono-data-tds4.0-cil libmono-db2-1.0-cil libmono-debugger-soft4.0a-cil 
  libmono-http4.0-cil libmono-i18n-cjk4.0-cil libmono-i18n-mideast4.0-cil libmono-i18n-other4.0-cil 
  libmono-i18n-rare4.0-cil libmono-i18n-west4.0-cil libmono-i18n4.0-all libmono-i18n4.0-cil 
  libmono-ldap4.0-cil libmono-management4.0-cil libmono-messaging-rabbitmq4.0-cil libmono-messaging4.0-cil 
  libmono-microsoft-build-engine4.0-cil libmono-microsoft-build-framework4.0-cil 
  libmono-microsoft-build-tasks-v4.0-4.0-cil libmono-microsoft-build-utilities-v4.0-4.0-cil 
  libmono-microsoft-build4.0-cil libmono-microsoft-csharp4.0-cil libmono-microsoft-visualc10.0-cil 
  libmono-microsoft-web-infrastructure1.0-cil libmono-oracle4.0-cil libmono-parallel4.0-cil 
  libmono-peapi4.0a-cil libmono-posix4.0-cil libmono-profiler libmono-rabbitmq4.0-cil 
  libmono-relaxng4.0-cil libmono-security4.0-cil libmono-sharpzip4.84-cil libmono-simd4.0-cil 
  libmono-smdiagnostics0.0-cil libmono-sqlite4.0-cil libmono-system-componentmodel-composition4.0-cil 
  libmono-system-componentmodel-dataannotations4.0-cil libmono-system-configuration-install4.0-cil 
  libmono-system-configuration4.0-cil libmono-system-core4.0-cil 
  libmono-system-data-datasetextensions4.0-cil libmono-system-data-entity4.0-cil 
  libmono-system-data-linq4.0-cil libmono-system-data-services-client4.0-cil 
  libmono-system-data-services4.0-cil libmono-system-data4.0-cil libmono-system-deployment4.0-cil 
  libmono-system-design4.0-cil libmono-system-drawing-design4.0-cil libmono-system-drawing4.0-cil 
  libmono-system-dynamic4.0-cil libmono-system-enterpriseservices4.0-cil 
  libmono-system-identitymodel-selectors4.0-cil libmono-system-identitymodel4.0-cil 
  libmono-system-io-compression-filesystem4.0-cil libmono-system-io-compression4.0-cil 
  libmono-system-json-microsoft4.0-cil libmono-system-json4.0-cil libmono-system-ldap-protocols4.0-cil 
  libmono-system-ldap4.0-cil libmono-system-management4.0-cil libmono-system-messaging4.0-cil 
  libmono-system-net-http-formatting4.0-cil libmono-system-net-http-webrequest4.0-cil 
  libmono-system-net-http4.0-cil libmono-system-net4.0-cil libmono-system-numerics-vectors4.0-cil 
  libmono-system-numerics4.0-cil libmono-system-reactive-core2.2-cil 
  libmono-system-reactive-debugger2.2-cil libmono-system-reactive-experimental2.2-cil 
  libmono-system-reactive-interfaces2.2-cil libmono-system-reactive-linq2.2-cil 
  libmono-system-reactive-observable-aliases0.0-cil libmono-system-reactive-platformservices2.2-cil 
  libmono-system-reactive-providers2.2-cil libmono-system-reactive-runtime-remoting2.2-cil 
  libmono-system-reactive-windows-forms2.2-cil libmono-system-reactive-windows-threading2.2-cil 
  libmono-system-reflection-context4.0-cil libmono-system-runtime-caching4.0-cil 
  libmono-system-runtime-durableinstancing4.0-cil 
  libmono-system-runtime-serialization-formatters-soap4.0-cil libmono-system-runtime-serialization4.0-cil 
  libmono-system-runtime4.0-cil libmono-system-security4.0-cil 
  libmono-system-servicemodel-activation4.0-cil libmono-system-servicemodel-discovery4.0-cil 
  libmono-system-servicemodel-internals0.0-cil libmono-system-servicemodel-routing4.0-cil 
  libmono-system-servicemodel-web4.0-cil libmono-system-servicemodel4.0a-cil 
  libmono-system-serviceprocess4.0-cil libmono-system-threading-tasks-dataflow4.0-cil 
  libmono-system-transactions4.0-cil libmono-system-web-abstractions4.0-cil 
  libmono-system-web-applicationservices4.0-cil libmono-system-web-dynamicdata4.0-cil 
  libmono-system-web-extensions-design4.0-cil libmono-system-web-extensions4.0-cil 
  libmono-system-web-http-selfhost4.0-cil libmono-system-web-http-webhost4.0-cil 
  libmono-system-web-http4.0-cil libmono-system-web-mobile4.0-cil libmono-system-web-mvc3.0-cil 
  libmono-system-web-razor2.0-cil libmono-system-web-regularexpressions4.0-cil 
  libmono-system-web-routing4.0-cil libmono-system-web-services4.0-cil 
  libmono-system-web-webpages-deployment2.0-cil libmono-system-web-webpages-razor2.0-cil 
  libmono-system-web-webpages2.0-cil libmono-system-web4.0-cil 
  libmono-system-windows-forms-datavisualization4.0a-cil libmono-system-windows-forms4.0-cil 
  libmono-system-windows4.0-cil libmono-system-workflow-activities4.0-cil 
  libmono-system-workflow-componentmodel4.0-cil libmono-system-workflow-runtime4.0-cil 
  libmono-system-xaml4.0-cil libmono-system-xml-linq4.0-cil libmono-system-xml-serialization4.0-cil 
  libmono-system-xml4.0-cil libmono-system4.0-cil libmono-tasklets4.0-cil libmono-webbrowser4.0-cil 
  libmono-webmatrix-data4.0-cil libmono-windowsbase4.0-cil libmono-xbuild-tasks4.0-cil libmonoboehm-2.0-1 
  libmonosgen-2.0-1 libmonosgen-2.0-dev libnunit-cil-dev libnunit-console-runner2.6.3-cil 
  libnunit-core-interfaces2.6.3-cil libnunit-core2.6.3-cil libnunit-framework2.6.3-cil 
  libnunit-mocks2.6.3-cil libnunit-util2.6.3-cil mono-4.0-gac mono-4.0-service mono-csharp-shell mono-devel 
  mono-gac mono-mcs mono-runtime mono-runtime-common mono-runtime-sgen mono-utils mono-xbuild mono-xsp4 
  mono-xsp4-base monodoc-base monodoc-http monodoc-manual 
Use 'sudo apt autoremove' to remove them. 
The following additional packages will be installed: 
  mono-devel 
The following NEW packages will be installed: 
  mono-devel 
0 upgraded, 1 newly installed, 0 to remove and 83 not upgraded. 
172 not fully installed or removed. 
Need to get 0 B/28.6 MB of archives. 
After this operation, 119 MB of additional disk space will be used. 
Do you want to continue? [Y/n] y 
Selecting previously unselected package mono-devel. 
(Reading database ... 490333 files and directories currently installed.) 
Preparing to unpack .../mono-devel_6.8.0.105+dfsg-3.3_all.deb ... 
Unpacking mono-devel (6.8.0.105+dfsg-3.3) ... 
dpkg: error processing archive /var/cache/apt/archives/mono-devel_6.8.0.105+dfsg-3.3_all.deb (--unpack): 
 trying to overwrite '/usr/bin/disco', which is also in package discodos 1.0~rc2-2 
dpkg-deb: error: paste subprocess was killed by signal (Broken pipe) 
Errors were encountered while processing: 
 /var/cache/apt/archives/mono-devel_6.8.0.105+dfsg-3.3_all.deb 
E: Sub-process /usr/bin/dpkg returned an error code (1)

[/FONT]
```

---

### Post by ryankm on 2023-10-27
autoremove doesn't work either.

```
[FONT=monospace][COLOR=#54ff54]**ryanm@ryan-GLBWR-RRRSSSCCC**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ sudo apt autoremove mono-complete [/COLOR]
Reading package lists... Done 
Building dependency tree... Done 
Reading state information... Done 
Package 'mono-complete' is not installed, so not removed 
You might want to run 'apt --fix-broken install' to correct these. 
The following packages have unmet dependencies: 
 mono-xsp4-base : Depends: mono-devel but it is not going to be installed 
[COLOR=#ff5454]**E: **[/COLOR][COLOR=#000000]Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution). [/COLOR]
[COLOR=#54ff54]**ryanm@ryan-GLBWR-RRRSSSCCC**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ sudo apt autoremove mono-xsp4 [/COLOR]
Reading package lists... Done 
Building dependency tree... Done 
Reading state information... Done 
You might want to run 'apt --fix-broken install' to correct these. 
The following packages have unmet dependencies: 
 mono-xsp4-base : Depends: mono-devel but it is not going to be installed 
 monodoc-http : Depends: mono-xsp4 but it is not going to be installed or 
                         mono-apache-server4 but it is not going to be installed or 
                         mono-fastcgi-server4 but it is not going to be installed 
[COLOR=#ff5454]**E: **[/COLOR][COLOR=#000000]Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution). [/COLOR]
[COLOR=#54ff54]**ryanm@ryan-GLBWR-RRRSSSCCC**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ sudo apt autoremove mono-devel [/COLOR]
Reading package lists... Done 
Building dependency tree... Done 
Reading state information... Done 
Package 'mono-devel' is not installed, so not removed 
You might want to run 'apt --fix-broken install' to correct these. 
The following packages have unmet dependencies: 
 mono-xsp4-base : Depends: mono-devel but it is not going to be installed 
[COLOR=#ff5454]**E: **[/COLOR][COLOR=#000000]Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).[/COLOR]


[/FONT]
```

---

### Post by ryankm on 2023-10-28
Okay so there is a problem with the Ubuntu Lunar Canonical repository and not posting an update... How do i completely remove wine mono so I can go back to having a PC?

---

