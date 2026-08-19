Tuan Muhammad Faiz Bin Tuan Rashid (Postman + Newman)

# Section 2: API Test

Candidate required to prepare a runnable API test by using any tool of their choice. Eg: Postman, Karate API tool.

Please provide instruction on how to open and execute the test files. PLEASE UPLOAD EXECUTABLE FILES for review. Eg: Postman collection, Karate API project, etc. 

The test scenarios will be given based on the following API documentation - https://gorest.co.in 

Scenario 1: 
Using https://gorest.co.in/public/v2/users
Create a new employee entry with Name, Gender, Email and Status (active or inactive) 
Verify id returned is in numerical format

Scenario 2:  
Using https://gorest.co.in/public/v2/users
Verify status for first entry is only either "active" or "inactive" 

(Request methods PUT, POST, PATCH, DELETE needs access token, which needs to be passed with 
"Authorization" header as Bearer token. Follow instruction in https://gorest.co.in/ to get access 
token)

## Files

- `postman/GoRest-API-Tests.postman_collection.json` — the test collection (2 requests, each with `pm.test` assertions)
- `postman/GoRest-Environment.postman_environment.json` — environment variables (`base_url`, `access_token`)
- `package.json` — npm script to run the collection via Newman

## 1. Get a GoRest access token

1. Go to https://gorest.co.in and sign in (e.g. with Google).
2. Open your account/profile page and generate a personal **Access Token**.
3. You'll paste this token in step 2 or 3 below — do not commit it anywhere public.

## 2. Run in the Postman GUI

1. Open Postman → **Import** → select both files in `postman/` (collection + environment).
2. In the top-right environment dropdown, select **GoRest Environment**.
3. Click the eye icon next to the dropdown → **Edit** → paste your access token into the `access_token` value → **Save**.
4. Open the **GoRest API Tests - Section 2** collection → click **Run** (collection runner).
5. Run it — both requests should complete with all tests passing (green checkmarks).

## 3. Run via Newman CLI

```bash
npm install
```

Set your token as an environment override (so it isn't stored in the file), then run:

```bash
npx newman run postman/GoRest-API-Tests.postman_collection.json \
  -e postman/GoRest-Environment.postman_environment.json \
  --env-var access_token=YOUR_TOKEN_HERE
```

Or, if you'd rather store the token directly in the environment file for convenience, edit the `value` field of `access_token` in `postman/GoRest-Environment.postman_environment.json`, then simply run:

```bash
npm test
```

Expected output: Newman's summary table reports 2 requests, 0 failed assertions.
