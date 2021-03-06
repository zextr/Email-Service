# Email-Service

> :pray: This is an official Oyewiki Email-Service to make your life easier when working with different email providers.

# Overview
Single Point of contact for following email services
- [AWS SES] (#aws-ses)
- [Send In Blue] (#send-in-blue)
- [Mail Jet] (#mail-jet)
- [Send Grid] (#send-grid)

Note: We use "rc" node module to define service specific configs.

## How To Use

1. ###AWS SES
	Integration Steps:

		1) Create ~/.config/awsses and save below mentioned object in this file for your details.
			{
			  "accessKeyId": "",//You AWS Access Key ID,
			  "secretAccessKey": "",//Your AWS Access Key,
			  "region": ""//Your AWS ACCESS Region
			}

		2) Take reference to ses email service
			var sesService = require("../emailProviders").ses;

		3) Call sendEmail method by creating sender and recipient data object as metioned below
			var data = {
				to : ["to1emailid@abc.com","to2emailid@abc.com"],
				from : "fromemailid@abc.com",
				subject : "AWS SES Service Demo",
				text : "Hi we are testing aws ses email service"
			};
			
			sesService.sendEmail(data, function(err, data){
				if(err){
					return done(err);
				}
				console.log(data);
				done();
			});

	For More details see mocha test cases **@ ./test/ses.js file.**

2. ###Send In Blue
	Integration Steps:

		1) Create ~/.config/sendinblue and save below mentioned object in this file for your details.
			{
				"url" : "", //API URL  Provided by SendInBlue,
				"access_key" : "", //Access Key Provided by SendInBlue,
				"timeout" : 5000 //Set timeout for API calls
			}

		2) Take reference to ses email service
			var sendInBlueService = require("../emailProviders").sendInBlue;

		3) Call sendEmail method by creating sender and recipient data object as metioned below
			var data = {
				to : {"toemailid@abc.com" : "to person name"},
				from : ["fromemailid@abc.com", "from person name"],
				subject : "Test Subject",
				html : "Hi we are testing sendInBlue email service"
			};
			
			sendInBlueService.sendEmail(data, function(data){
				console.log(data);
				done();
			});

3. ###Mail Jet
	//TO DO

4. ##Send Grid
	//TO DO

	For More details see mocha test cases **@ ./test/sendInBlue.js file.**

#Benefit
This can act as a single point of contact for all your emails.


#TODO

1. Integration of 
	- Mailjet
	- SendGrid
