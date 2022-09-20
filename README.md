# How to open a port on Google Cloud Platform

## For opening port for all instance

Login to your dashboard [here](https://console.cloud.google.com/). Select the search bar and enter `firewall`.

You will see something like this, click on the `Firewall`.![Screen Shot 2022-09-19 at 8.28.41 PM](https://github.com/zliu269/openPortGuideForGCP/blob/main/PortOpenGuide.assets/Screen%20Shot%202022-09-19%20at%208.28.41%20PM.png)Click `CREATE FIREWALL RULE`.

![Screen Shot 2022-09-19 at 8.31.03 PM](https://github.com/zliu269/openPortGuideForGCP/blob/main/PortOpenGuide.assets/Screen%20Shot%202022-09-19%20at%208.31.03%20PM.png)

Click the `Specified target tags` and change it to `All instances in the network`. The `Target tags` field will disappear. 

![Screen Shot 2022-09-19 at 8.34.12 PM](https://github.com/zliu269/openPortGuideForGCP/blob/main/PortOpenGuide.assets/Screen%20Shot%202022-09-19%20at%208.34.12%20PM.png)

In the `Source IPv4 ranges`, type in `0.0.0.0/0` to allow all IPs to connect to this port. You can also specify the **exact IP address** you want to allow to access this port by typing in the IP directly. (E.g., `192.168.1.1`)

Select your protocol and fill in the `Ports` field with your port. In the example the sock should use a TCP connection and the port should be `9999`.

Click create to finish creating the rule and the port should be open instantly.

![Screen Shot 2022-09-19 at 8.38.46 PM](https://github.com/zliu269/openPortGuideForGCP/blob/main/PortOpenGuide.assets/Screen%20Shot%202022-09-19%20at%208.38.46%20PM.png)

## For opening port on one or more instance(s)

First, go to your `VM instances`.

![image-20220919205239111](https://github.com/zliu269/openPortGuideForGCP/blob/main/PortOpenGuide.assets/image-20220919205239111.png)

Click your instance name.

![Screen Shot 2022-09-19 at 8.54.20 PM](https://github.com/zliu269/openPortGuideForGCP/blob/main/PortOpenGuide.assets/Screen%20Shot%202022-09-19%20at%208.54.20%20PM.png)

Then click `EDIT`.

![Screen Shot 2022-09-19 at 8.55.49 PM](https://github.com/zliu269/openPortGuideForGCP/blob/main/PortOpenGuide.assets/Screen%20Shot%202022-09-19%20at%208.55.49%20PM.png)

Under the `Networking` field, Fill in the `network tags` with your tag. Here, I am using `tag-1` as an example.

![Screen Shot 2022-09-19 at 8.57.57 PM](https://github.com/zliu269/openPortGuideForGCP/blob/main/PortOpenGuide.assets/Screen%20Shot%202022-09-19%20at%208.57.57%20PM.png)

Then go through the same firewall creating process, but change the `Targets` to `Specified Target Tags` and fill in the tag you just created.![Screen Shot 2022-09-19 at 8.34.12 PM](https://github.com/zliu269/openPortGuideForGCP/blob/main/PortOpenGuide.assets/Screen%20Shot%202022-09-19%20at%208.34.12%20PM.png)

The rest will be the same. And this should also work instantly.

## FAQ

### I did everything above but it still did not work?

A: Check your code. Change the server IP to `0.0.0.0` to allow it to be connected from outside.

