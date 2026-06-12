---
title: "OnPrem - Landscape using pull pockets fails with &quot;does not have a Release file&quot; and c"
date: 2023-05-24
forum: Installation &amp; Upgrades
---

### Post by scahartner on 2023-05-24
We ran into a problem using mirror and pull pockets on our landscape (v23.03) installation.
 After setting up our on-prem landscape server using the following commands

```
landscape-api create-distribution ubuntu
 landscape-api create-series   --pockets  release,updates,security  \``--components  main,restricted,universe,multiverse   --architectures amd64,i386  \``--gpg-key mirror-key   --mirror-uri [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)   \``--mirror-series focal focal ubuntu
 landscape-api sync-mirror-pocket release focal ubuntu
landscape-api sync-mirror-pocket updates focal ubuntu
landscape-api sync-mirror-pocket security focal ubuntu
```

**Create staging and production pockets**
```
landscape-api create-pocket --pull-pocket release release-staging focal ubuntu main,universe amd64,i386 pull mirror-key
landscape-api create-pocket --pull-pocket updates updates-staging focal ubuntu main,universe amd64,i386 pull mirror-key
landscape-api create-pocket --pull-pocket security security-staging focal ubuntu main,universe amd64,i386 pull mirror-key
landscape-api create-pocket --pull-pocket release-staging  release-production focal ubuntu main,universe amd64,i386 pull mirror-key
landscape-api create-pocket --pull-pocket updates-staging  updates-production focal ubuntu main,universe amd64,i386 pull mirror-key
landscape-api create-pocket --pull-pocket security-staging  security-production focal ubuntu main,universe amd64,i386 pull  mirror-key
```


**Create repository profiles**
```
landscape-api create-repository-profile --description "Staging profile used to evaluate" staging-profile
landscape-api associate-repository-profile --tags staging staging-profile
landscape-api create-repository-profile --description "Production profile used for production system" production-profile
landscape-api associate-repository-profile --tags production production-profile
```
[B]
Associate pockets with profiles[/B]
```
landscape-api add-pockets-to-repository-profile staging-profile release-staging,updates-staging,security-staging focal ubuntu
landscape-api add-pockets-to-repository-profile production-profile  release-production,updates-production,security-production focal ubuntu
```

 We then configured the SSL certifcates using certbot
 However when we try to update our clients using “apt update” we get the following errors[INDENT] [COLOR=#ff0000]The certificate chain uses expired certificate.  Could not handshake: Error in the certificate verification[/COLOR]
 [/INDENT]

While not ideal we got around this issue by removing the verification step via:

```
 touch /etc/apt/apt.conf.d/99verify-peer.conf && echo >>/etc/apt/apt.conf.d/99verify-peer.conf "Acquire { https::Verify-Peer false }
```

With the certificate issue out of the way we are now seeing the following errors on the clients:

```
[INDENT] E: The repository ‘[http://landscape.X.com/repository/standalone/ubuntu](http://landscape.X.com/repository/standalone/ubuntu) focal-release-production Release’ does not have a Release file.
N: Updating from such a repository can’t be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository ‘[http://landscape.X.com/repository/standalone/ubuntu](http://landscape.X.com/repository/standalone/ubuntu) focal-updates-production Release’ does not have a Release file.
N: Updating from such a repository can’t be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository ‘[http://landscape.X.com/repository/standalone/ubuntu](http://landscape.X.com/repository/standalone/ubuntu) focal-security-production Release’ does not have a Release file.
N: Updating from such a repository can’t be done securely, and is therefore disabled by default.[/INDENT]

```[INDENT]


 [/INDENT]
We are able to apply updates to the clients, just strange that we are seeing these errors.
 On the landscape server we see the following message in the apache access log

---

### Post by scahartner on 2023-05-24
[https://discourse.ubuntu.com/t/onprem-landscape-using-pull-pockets-fails-with-does-not-have-a-release-file-and-certificate-errors/35950]("https://discourse.ubuntu.com/t/onprem-landscape-using-pull-pockets-fails-with-does-not-have-a-release-file-and-certificate-errors/35950?u=scahartner")

---

### Post by scahartner on 2023-05-25
See dirsourse for details of solution.

Updating the ca-certificates was required as the landscape client was  a clean installation of Ubuntu 20.04 LTS without any patches applied.  Updating the ca-certs as described above got us pasted the SSL issues.
 You were correct in that the problem was with the apache configuration

 On a working installation of Landscape Server (23.03+9) the apache configuration contained:
 > <VirtualHost *:80>
  ...
  RewriteRule ^/(.*) https://landscape.testbed.local:443/$1 [R=permanent]
</VirtualHost>
 While on the problem system it had:
 > <VirtualHost *:80>
  ...
  RewriteRule ^/(.*) https://landscape.X.com:443/$1 [R=permanent]
  RewriteCond %{SERVER_NAME} =landscape.X.com
  RewriteRule ^ https://%{SERVER_NAME}%{REQUEST_URI} [END,NE,R=permanent]
</VirtualHost>
 Both of these were quick installed, however it could be that the  problem system was a fresh install of 23.03.9 while the working system  was upgraded from an earlier version.
 After commenting out extra 2 lines we were able to update the clients

---

