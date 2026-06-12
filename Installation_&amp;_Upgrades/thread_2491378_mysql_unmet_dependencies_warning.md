---
title: "mysql unmet dependencies warning"
date: 2023-10-06
forum: Installation &amp; Upgrades
---

### Post by charithanayana on 2023-10-06
hi...
it happend after removing 3rd party server link in software updater. after that mysql doesn't work and i try to unstall and re install. but can't install mysql server.
 i'm tried several times fix this problem but still same position. 

```
udo apt-get install mysql-serverReading package lists... DoneBuilding dependency tree... DoneReading state information... DoneSome packages could not be installed. This may mean that you haverequested an impossible situation or if you are using the unstabledistribution that some required packages have not yet been createdor been moved out of Incoming.The following information may help to resolve the situation:
The following packages have unmet dependencies: mysql-community-client : Depends: libssl1.1 (>= 1.1.1) but it is not installable                          Depends: mysql-community-client-core (= 8.0.34-1ubuntu20.04) but it is not going to be installed mysql-community-server-core : Depends: libssl1.1 (>= 1.1.1) but it is not installable                               Recommends: mecab-ipadic-utf8 but it is not going to be installedE: Unable to correct problems, you have held broken packages.
```
also doing sudo apt-get update this warring show in the terminal

```
Fetched 2,411 kB in 46s (52.7 kB/s)                                            Reading package lists... DoneW: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://repo.mysql.com/apt/ubuntu focal InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 467B942D3A79BD29W: Failed to fetch http://repo.mysql.com/apt/ubuntu/dists/focal/InRelease  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 467B942D3A79BD29W: Some index files failed to download. They have been ignored, or old ones used instead.

```
remove and re add the PUBKEY it also not solved.

any idea friends?

---

### Post by ActionParsnip on 2023-10-06
Why are you adding an extra repo? MySQL is in the default Ubuntu repos

---

