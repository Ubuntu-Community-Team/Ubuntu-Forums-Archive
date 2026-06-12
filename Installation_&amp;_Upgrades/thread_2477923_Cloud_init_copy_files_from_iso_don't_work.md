---
title: "Cloud init copy files from iso don't work"
date: 2022-08-11
forum: Installation &amp; Upgrades
---

### Post by hellboy11 on 2022-08-11
[FONT=arial]
[/FONT][COLOR=#232629][FONT=-apple-system][FONT=arial][B]Hi everyone,
I'm looking for a way to copy file from the automate installation of ubuntu20/ubuntu22 LTS. I created special ISO with user-data commands but the when I am trying to do is to copy a file to a specific directory it seems working but after the restart when you finish the installation I don't see the file in the path any more. Thanks in advanced
late-commands:
    - |
      sudo mkdir /mnt/lp1
      sudo mount -o loop /dev/cdrom /mnt/lp1
      ls -lha /mnt/lp1
      sudo cp /mnt/lp1/katello_server-host-cert.crt /usr/local/share/ca-certificates/katello_server-host-cert.crt
      sudo umount /mnt/lp1
      sudo update-ca-certificates
      cat <<EOF > /target/etc/cloud/cloud.cfg.d/80_my.cfg
      hostname: ubuntu-$(openssl rand -hex 3)
      manage_etc_hosts: true
      preserve_hostname: false
      EOF

  ls -lha /mnt/lp1 >>> in this line I can see the files of the iso but the cp dont work[/B] 


[https://i.stack.imgur.com/TBXgt.png](https://i.stack.imgur.com/TBXgt.png)[/FONT]
[/FONT][/COLOR]

---

### Post by sudodus on 2022-08-12
Hi,

This post is mainly a bump, to bring attention to your thread. Unfortunately I have nothing new to suggest right now. I hope that someone with experience of 'cloud init' will see your thread and help you :-)

---

