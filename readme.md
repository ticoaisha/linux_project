# DevOps Linux Project

We will be learning how to set up web server and configure it to host our own website.

**1. Step 1. Launch EC2 instance**

EC2 is an AWS service that allows you to create servers in the cloud. We will use it to launch the web server.

The following configuration will be applied:

![](/linux_project/images/1_ec2.png)

![](/linux_project/images/2_ec2_key_pair.png)

![](/linux_project/images/3_ec2_network_settings.png)

SSH is a protocol used to connect to the remote Linux servers, whereas HTTP and HTTPS are the protocols used to access websites on the web server.

Next, let's launch the an instance. 

![](/linux_project/images/4_ec2_launched.png)

The instance needs to be in the "Running" state in order to connect to the instance.

![](/linux_project/images/5_connect_to_ec2_instance.png)

We will use "EC2 Instance Connect" to connect to the instance.

![](/linux_project/images/6_ec2_connect.png)

![](/linux_project/images/7_connected_to_ec2_inst.png)

Note: If you will not be able to connect to the instance, then you need to check your Security Group configuration and make sure that Port 22 is open. 

**2. Step 2. Install Apache Webserver**

When we are launching the instance, first thing that we need to do is to update the packages by running 
`sudo apt update && sudo apt upgrade`

![](/linux_project/images/8_update_packages.png)

![](/linux_project/images/9_updated_packages.png)

After everything has been updated, let's run the command to install an apache web server by running:
`sudo apt install apache2`

![](/linux_project/images/10_install_apache_server.png)

Once it is installed, we should see a test page to confirm that it is installed. 
If we want to check is apache has been installed, we can run the following command:
`which apache2`:

![](/linux_project/images/11_which.png)

Also we can run `apache2 -v`:

![](/linux_project/images/12_apache_v.png)

Now we can start the service by running: `sudo service apache2 start`:

![](/linux_project/images/13_apache_start.png)

We can check the status by running: `sudo service apache2 status`

![](/linux_project/images/14_apache_status.png)

Also I can copy and paste Puplic IP into a new tab of the browser and Apache default page should be displayed:

![](/linux_project/images/15_public_ip.png)

![](/linux_project/images/16_apache_default_page.png)

This is a test page. Now you need to customize it to show your own content.

As we can see from the test page, we need to replace this file to have our own web page:

![](/linux_project/images/17_replace_file.png)

Let's go to that path and then check the content of `html`:

![](/linux_project/images/18_go_to_html_path.png)

We need to remove it by running: `sudo rm index.html`:

![](/linux_project/images/19_remove_index_html.png)

Now we want to have our own html file:

![](/linux_project/images/20_nano_index_html.png)

![](/linux_project/images/21_index_html_in_nano.png)

Type in the editor and save it

![](/linux_project/images/22_type_in_editor.png)

Now we will restart apache server by running the following command: `sudo service apache2 restart` and check the status as well:

![](/linux_project/images/23_apache_restart.png)

After this, if we will go the apache default page and refresh it, we will see the content that we typed in `index.html` in nano editor:

![](/linux_project/images/24_our_content_index_html.png)

Now we can customize this `html` file. We will use code provided. We will copy html code and paste into the `index.html` file:

![](/linux_project/images/25_nano_to_edit_html_file.png)

![](/linux_project/images/26_paste_html.png)

Save and exit out of nano, restart the service again

![](/linux_project/images/27_restart_check_the_status.png)

If we will go to the webpage and refresh it, we will see our simple html page:

![](/linux_project/images/28_simple_webpage.png)

This IP address we can map with the DNS name.

Let's not forget to delete our EC2 instance.






