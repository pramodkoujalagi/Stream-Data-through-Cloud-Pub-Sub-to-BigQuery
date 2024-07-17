# Stream Data through Cloud Pub/Sub to BigQuery

1. Create a bucket matching your project name (e.g. gs://playground-s-11-78f5b410)
2. Leave other settings as default

### UPDATED STEPS:
3. Go to IAM and copy the compute service account name to a text editor (e.g. 526273785053-compute@developer.gserviceaccount.com)
4. Create a Pub/Sub topic named "purchases"
5. Copy the default subscription name to a text editor (e.g. projects/playground-s-11-78f5b410/subscriptions/purchases-sub)
6. Go to Big Query and create a dataset
7. Create a table and add the schema, and copy the table ID (e.g. playground-s-11-78f5b410:trends.purchases)
8. Create a data-flow job with max workers=1, number of workers = 1, Machine type n1-standard-1
9. The job will create, but then throw a credentials issue (this is because the Dataflow API had not finished enabling before the job tried to run)
10. Click on CLONE and then create another copy - the second job will run correctly.
11. Open Cloud Shell, run sudo pip3 install google-cloud-pubsub and the open the Shell editor, to create transactions.py and copy in MOCK_DATA.csv as per the lesson video
12. Run python3 transactions.py
13. Use Big Query to query the data which will now have been synced into the purchases table.
