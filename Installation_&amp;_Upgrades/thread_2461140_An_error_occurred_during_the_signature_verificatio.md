---
title: "An error occurred during the signature verification Google Cloud SKD"
date: 2021-04-25
forum: Installation &amp; Upgrades
---

### Post by nor-wanderer on 2021-04-25
Hi there,

I'm getting the following error when running sudo apt update on Ubuntu 20.04:
```
Get:6 http://packages.cloud.google.com/apt cloud-sdk InRelease [6&#8239;739 B]                         
Err:6 http://packages.cloud.google.com/apt cloud-sdk InRelease                                                   
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY FEEA9169307EA071 NO_PUBKEY 8B57C5C2836F4BEB
```
Then followed by:
```
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://packages.cloud.google.com/apt](http://packages.cloud.google.com/apt) cloud-sdk InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY FEEA9169307EA071 NO_PUBKEY 8B57C5C2836F4BEB
W: Failed to fetch [http://packages.cloud.google.com/apt/dists/cloud-sdk/InRelease](http://packages.cloud.google.com/apt/dists/cloud-sdk/InRelease)  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY FEEA9169307EA071 NO_PUBKEY 8B57C5C2836F4BEB
W: Some index files failed to download. They have been ignored, or old ones used instead.
```
I understand I need to update a key or several keys somewhere, but haven't been able to figure out exactly how to go about it, and what commands to run.
Any suggestions whould be highly appreciated.

---

### Post by nor-wanderer on 2021-04-25
I found a similar issue in different thread.
This command solved it for me:
```
sudo curl [https://packages.cloud.google.com/apt/doc/apt-key.gpg](https://packages.cloud.google.com/apt/doc/apt-key.gpg) | sudo apt-key --keyring /usr/share/keyrings/cloud.google.gpg add -
```
Apparantely this is the officially documented way to add the current key, as found e.g. on [https://cloud.google.com/sdk/docs/install#deb](https://cloud.google.com/sdk/docs/install#deb)

---

