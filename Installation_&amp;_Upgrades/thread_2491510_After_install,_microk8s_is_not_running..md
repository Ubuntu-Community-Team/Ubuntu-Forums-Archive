---
title: "After install, microk8s is not running."
date: 2023-10-11
forum: Installation &amp; Upgrades
---

### Post by gerryseidl on 2023-10-11
[COLOR=#1F2328][FONT=-apple-system]After install, microk8s is not running.[/FONT][/COLOR]
[COLOR=#1F2328][FONT=-apple-system]Running - microk8s kubectl get all --all-namespaces shows that components are not running.[/FONT][/COLOR]
[FONT=-apple-system, BlinkMacSystemFont, Segoe UI, Noto Sans, Helvetica, Arial, sans-serif, Apple Color Emoji, Segoe UI Emoji][COLOR=#1f2328]I tried to stop and start, and also reboot. No change.[/COLOR][/FONT]

[FONT=-apple-system, BlinkMacSystemFont, Segoe UI, Noto Sans, Helvetica, Arial, sans-serif, Apple Color Emoji, Segoe UI Emoji][COLOR=#1f2328]I've attached the inspection report. I'd really appreciate assistance to get this up and running.[/COLOR][/FONT]

---

### Post by MAFoElffen on 2023-10-11
This was installed as a Snap app?

What does mircrok8s show as status via
```

microk8s status

```
The output should look similar to this
```

microk8s is running
high-availability: no
  datastore master nodes: 127.0.0.1:19001
  datastore standby nodes: none
addons:
  enabled:
    ha-cluster           # (core) Configure high availability on the current node
  disabled:
    community            # (core) The community addons repository
    dashboard            # (core) The Kubernetes dashboard
    dns                  # (core) CoreDNS
    gpu                  # (core) Automatic enablement of Nvidia CUDA
    helm                 # (core) Helm 2 - the package manager for Kubernetes
    helm3                # (core) Helm 3 - Kubernetes package manager
    host-access          # (core) Allow Pods connecting to Host services smoothly
    hostpath-storage     # (core) Storage class; allocates storage from host directory
    ingress              # (core) Ingress controller for external access
    mayastor             # (core) OpenEBS MayaStor
    metallb              # (core) Loadbalancer for your Kubernetes cluster
    metrics-server       # (core) K8s Metrics Server for API access to service metrics
    prometheus           # (core) Prometheus operator for monitoring and logging
    rbac                 # (core) Role-Based Access Control for authorisation
    registry             # (core) Private image registry exposed on localhost:32000
    storage              # (core) Alias to hostpath-storage add-on, deprecated

```
What happens when you ask Kubernetes directly?
```

kubectl get pods --all-namespaces

```
To narrow down if it is microk8s or kubernetes...

---

### Post by gerryseidl on 2023-10-12
Yes, snap install via 'sudo snap install microk8s --classic'.

microk8s status comes back with -- microk8s is not running. Use microk8s inspect for a deeper inspection.

I included the tar from that in this thread.

I have provided screen shots of the getall output.

---

### Post by MAFoElffen on 2023-10-12
The 2 common things I see for "microk8s not running" is that it needs at least 512k to start and that the ports for it are not opened up in the firewall.

The ports that need to be open are
```

16443    API server
10250    kubelet
10255    kubelet
25000    cluster-agent

```
That is what they say (the microk8s doc's), but others say the APPI port is actually 6443. Yes, I confirmed, Kubernets kubelet doc's say the default port for the API is 6443, but microk8S Doc's mistakenly say they are 16443...
RE: [https://kubernetes.io/docs/concepts/security/controlling-access/#transport-security](https://kubernetes.io/docs/concepts/security/controlling-access/#transport-security)

Look at /etc/kubernetes/kubelet.conf and make sure the ports are correct there. If you change it there, then after the change, do:
```

systemctl daemon-reload 
systemctl restart kubelet

```
IDK, maybe there is a problem there, with them not talking with each other, uncovered by each of their doc's pointing to different ports for the kubelet API. Maybe you should try both of those ports, alternatively, and test what works or not.

---

### Post by gerryseidl on 2023-10-12
I opened the ports with sudo ufw allow #/tcp and restarted microk8s but no affect. Still not running.
I do not have a [COLOR=#000000]/etc/kubernetes/kubelet.conf file. [/COLOR]

---

### Post by MAFoElffen on 2023-10-12
Dang.

If it were me... I would submit the tar in a new issue to: [https://github.com/canonical/microk8s/issues](https://github.com/canonical/microk8s/issues)

The last issue of that not starting was 3 days ago, but is a different problem. His worked for 2 weeks, then stopped working. "Your's" never has worked.

The tip there, after reviewing their "Issues" on that... A lot of their Issues there seem to close from being stagnent from being abandoned or inactivity, rather than from actually being resolved. People seem to give up too early.

So once you start an issue there, latch onto them like a "pit bull" and do not let go. If they do not give you answer in due time, bump the comments and ask them when you should expect a response, so that their Issue Tracker doesn't time out.

This is the same thing I have to do with upstream Intel Engineers in their Support Teams, so that they know I am serious, and I am not going away until things are resolved. That seems drastic, but... I remain professional and diplomatic... But always there, as a reminder. It works.

I do the same at LaunchPad

---

### Post by gerryseidl on 2023-10-13
I have already done that but no one is picking it up :\


Thanks for your help :)

---

### Post by MAFoElffen on 2023-10-13
> **gerryseidl said:**
> I have already done that but no one is picking it up :\

Thanks for your help :)
Can you link it here please, so we can connect it, I can follow the issue, and maybe possibly email someone there to try to prompt at least some kind of activity?

I just think "some things" are the right thing to do.

Nevermind. I see it: [https://github.com/canonical/microk8s/issues/4248](https://github.com/canonical/microk8s/issues/4248)

Messaged one of the contributors, who is in my network... Though he might not see this until Monday, his timezone.

---

### Post by MAFoElffen on 2023-10-16
> **MAFoElffen said:**
> Nevermind. I see it: [https://github.com/canonical/microk8s/issues/4248](https://github.com/canonical/microk8s/issues/4248)

Messaged one of the contributors, who is in my network... Though he might not see this until Monday, his timezone.
The Senior Canonical Engineer there, I talked with him a bit yesterday. We talked about this... From there we got into a discussion on Ubuntu Pro Support itself.

We both cannot reproduce your error, so it is not a "bug" in Microk8s, but rather a configuration error on your machine somewhere. Since not a bug, he is not going to help there, unless you have Ubuntu Pro Support.

His recommends were to recheck all your configuration settings.

---

